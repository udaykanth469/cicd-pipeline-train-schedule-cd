# cicd-pipeline-train-schedule-cd

This is a simple train schedule app written using nodejs. It is intended to be used as a sample application for a series of hands-on learning activities.

## Running the app

You need a Java JDK 7 or later to run the build. You can run the build like this:

    ./gradlew build

You can run the app with:

    ./gradlew npm_start

Once it is running, you can access it in a browser at [http://localhost:3000](http://localhost:3000).

# Instructions
Your team is working on the train-schedule app. A Jenkins Pipeline has already been created for the app, but all it does right now is run a continuous integration build. The team has asked you to add automated deployments to a staging server, and to add a production server to the pipeline. The team has decided to use the master branch of the git repository to control deployments, so only changes to the master branch should be deployed. Whenever there is a change to the master branch, the Pipeline needs to do the following after the CI build is completed:

Deploy the application to a Staging server.
Wait for approval before deploying to Production.
Once approval is provided, deploy to Production.
Begin by creating a fork of the source code at: https://github.com/linuxacademy/cicd-pipeline-train-schedule-cd

You can find a sample solution Jenkinsfile under the example-solution branch.

In order to complete this learning activity, you will need to:

Deploy the app to the staging server via the Jenkins pipeline.
Configure the staging and production servers for the Publish Over SSH plugin.
Add a credential to Jenkins called webserver_login to allow Jenkins to authenticate with the web servers. The user has already been created on the web servers with the username deploy and the password jenkins.
Create a multibranch pipeline project called train-schedule and set it up to build from your GitHub fork.
Create a stage in the Jenkinsfile to deploy the app to the staging server.
Run the build to deploy to the staging server.
Deploy the app to the production server via the Jenkins pipeline:
Create a stage to deploy to production after awaiting user input.
Run the build.
Approve the deployment to production.
A few notes about the lab server setup:

A systemd service called train-schedule has already been created on both web servers. The train-schedule app can be controlled with systemd using commands like systemctl stop train-schedule and systemctl start train-schedule.
The train-schedule service expects the application code to be deployed to /opt/train-schedule.
A deployment user has already been created on both web servers. It can write to /opt/train-schedule as well as start and stop the train-schedule service. The username is deploy and the password is jenkins. Jenkins can use these credentials in order to perform the deployment.
The Publish Over SSH plugin is already installed on the Jenkins server.
The Jenkins server listens on port 8080. Train Schedule, once it is deployed, will listen on port 3000.
