pipeline {
    agent any

    tools {
        jdk 'jdk17'
        gradle 'gradle-8.7'
    }

    environment {
        DB_HOST = "${env.DB_HOST}"
        DB_NAME = "${env.DB_NAME}"
        DB_USER = "${env.DB_USER}"
        DB_PASS = "${env.DB_PASS}"
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'matser',
                    url: 'https://github.com/totoruudev/springboot-app'
            }
        }

        stage('Build') {
            steps {
                bat 'gradle clean build'
            }
        }

        stage('Test') {
            steps {
                bat 'gradle test'
            }
        }

        stage('Run') {
            steps {
                bat 'java -jar build\\libs\\springboot-app-0.0.1-SNAPSHOT.jar'
            }
        }
    }
}