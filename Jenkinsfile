#!/usr/bin.env groovy

pipeline {   
    agent any
    stages {
        stage("test") {
            steps {
                script {
                    echo "Testing the application..."

                }
            }
        }
        stage("build") {
            steps {
                script {
                    echo "Building the application..."
                }
            }
        }

        stage("deploy") {
            steps {
                script {
                    def dockerCmd = "docker run -d -p 8080:80 sofiavistas/react-counter-app:latest"
                    sshagent(['ec2-server-key']) {
                        sh "ssh -o StrictHostKeyChecking=no  ec2-user@13.61.146.89 ${dockerCmd}"
                    }
                }
            }
        }               
    }
} 
