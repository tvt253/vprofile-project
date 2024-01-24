FROM openjdk:11 AS build_image

WORKDIR /app

RUN apt update && apt install maven -y
RUN git clone https://github.com/tvt253/vprofile-project.git
RUN cd vprofile-project && git checkout docker && mvn install

FROM tomcat:9.0-jre11

#RUN rm -r /usr/local/tomcat/webapps/*
COPY --from=build_image /app/vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]
