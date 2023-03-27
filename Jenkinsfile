def gv

pipeline {
    agent any
    stages {
        stage("init") {
            steps {
                script {
                    gv = load "script.groovy"
                }
            }
        }
        stage("build jar") {
            steps {
                script {
                    echo "building jar"
                    //gv.buildJar()
                }
            }
        }
        stage("build image") {
            steps {
                script {
                    echo "building image"
                    //gv.buildImage()
                }
            }
        }
        stage("deploy") {
            steps {
                script {
                    echo "deploying"
                    def dockerCmd = 'docker run -p 3080:3080 -d pavangudiwada/techworldwithnana:v1'
                    sshagent(['ec2-server-key']){
                        ssh "ssh -o StrictHostKeyChecking=no ec2-user@44.211.47.92 $(dockerCmd)"
                    }
                    //gv.deployApp()
                }
            }
        }
    }   
}
