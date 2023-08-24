FROM openjdk:11 AS Build_Image

RUN apt update && apt install maven -y

RUN git clone https://github.com/ritesh-kumar-nayak/vprofile-project-forked.git

RUN cd vprofile-project-forked && git checkout docker && mvn install


FROM tomcat:9-jre11

LABEL project="Vpro"
LABEL Author="Ritesh"

RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=Build_Image vprofile-project-forked/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD [ "catalina.sh", "run" ]
