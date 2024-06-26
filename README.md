# README #

## What this project is about ##
In this project, our goal is to convert a renowned program analysis tool, [Hydrogen](https://github.com/iowastateuniversity-programanalysis/hydrogen), into a web-based platform and present the program analysis results of Hydrogen to the end-users. The interface allows users to upload a few versions of software and select which pairs to analyze. Then, the web interface will display the statistics of MVICFG and visualizations of a certain part of MVICFG based on the location information using an interactive manner. As demonstrated in the paper ["Patch verification via multiversion interprocedural control flow graphs](https://dl.acm.org/doi/abs/10.1145/2568225.2568304 ), the web-based platform depicts the data collected from constructing MVICFGs such as the number of versions and size of the first version in the benchmarks, the number of program versions, the average number of added and removed statements between any two consecutive versions as churn, time used, and memory overhead, etc.

## Technology and Frameworks being used in this project ##
1. Spring Boot has the charge of managing server-side code
2. Spotify docker-client has been used to communicate with the docker instance
3. Maven used as a build and dependency management tool
4. Template engine Thyemleaf used for HTML rendering
5. For UI design, Bootstrap and Font-awesome have been used

## Dependencies ##
1. Apache Maven(Version: 3.3.9)
2. Apache Tomcat (Version: 8)
3. JDK (Version: 1.8)


## Project Structure ##
1. /src/main/resources/ - contains client-side code
2. /src/main/resources/templates/ - contains HTML code
3. /src/main/resources/static/ - contains CSS and necessary javascript code
4. /src/main/java/com/iastate/web/hydrogen - contains server-side code written in the spring boot framework of Java programming language
5. /hydrogen_analysis/user_program - a temporary directory containing files uploaded by the user
6. /hydrogen_analysis/hydrogen_output - the result of hydrogen analysis
7. /src/main/resources/application.properties - Use this file to configure the application. (Described in next section)


## Configuring application ##
To configure the application, open /src/main/resources/application.properties and modify as follows:
1. docker.id: Provide running docker instance ID (You can obtain docker instance ID by running this command in terminal: docker ps)
2. hydrogen.path: Path of Hydrogen base path in docker
3. file.upload.directory: Location where uploaded files will be stored temporarily
4. hydrogen.output.directory: Location where analysis result of Hydrogen will be stored temporarily
5. docker.test.directory: A directory created in the docker Hydrogen base path to move uploaded user files
6. server.port: The port at which the application will be running

 
## Deploy application in a servlet container ##
1. Go to the root directory of the project
2. Open the shell and type the following command: ./mvnw clean package
3. Go to the target directory and copy hydrogen-0.0.1-SNAPSHOT.war
4. Paste it to any servlet container. For Tomcat, paste it in web apps folder and start Tomcat
5. You should be able to access the application in the following URL: http://localhost:9080/hydrogen/ 
6. The landing page provides a prompt to the user to upload a zipped folder containing c files


## Run application with embedded tomcat ##
1. Go to the root directory of the project
2. Open the shell and type the following command: ./mvnw clean spring-boot:run
3. The application will be deployed at default port 9080 (If available). 
4. If port 9080 is not available, you can run with the port of your choice with command line arguments. For example, to run in port 9070, type: ./mvnw clean spring-boot:run -Drun.arguments="--server.port=9070"

## Instructions for uploading zip file:
1. Create an empty folder.
2. Move all c files inside that empty directory.
3. Archive the folder. It should have a .zip extension.
4. Upload the zipped folder on the website.

## What's good about this project? ##
1. Leveraged MVC software architectural pattern, thereby making it easily extensible, modular, transferable, and scalable.
2. Leveraged cutting-edge technologies on every front, easing the potential of incorporating the latest powerful features in the application. 
