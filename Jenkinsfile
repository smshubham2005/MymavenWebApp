pipeline {
    agent any

    tools {
        maven 'MAVEN'
        jdk 'JDK' // Adding JDK back in case your build environment needs it
    }

    stages {
        stage('Checkout') {
            steps {
                // Update this URL to YOUR GitHub repository for the WebApp
                git branch: 'main', url: 'https://github.com/smshubham2005/MyMavenWebApp.git'
            }
        }

        stage('Build & Package') {
            steps {
                // This creates the .war file seen in your 'tree' output
                sh 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                // Runs unit tests if you have any in src/test/java
                sh 'mvn test'
            }
        }

        stage('Archive Artifacts') {
            steps {
                // Instead of "Running", we save the .war file so you can download it from Jenkins
                               sh 'cp target/MymavenWebApp.war /opt/tomcat/webapps/'

            }
        }
    }

    post {
        success {
            echo 'WebApp build and packaging successful!'
        }
        failure {
            echo 'Build failed! Check the pom.xml or console logs.'
        }
    }
}
