pipeline{
    agent any
    
    tools{
        maven "my-maven"
    }
    stages{

        stage("Clone App from Git"){
            steps{
                echo "====++++  Clone App from Git ++++===="
                git branch:"master", url: "https://github.com/val7304/pipeline-jenkins-vagrant-ansible-app.git"
              }          
        }

        stage("Build and Package"){
            steps{
                echo "====++++  Build and Unit Test (Maven/JUnit) ++++===="
                sh "mvn -f greetings-app/pom.xml clean package"
            }           
        }
        
        stage("Static Code Analysis (SonarQube)"){
            steps{
                echo "====++++  Static Code Analysis (SonarQube) ++++===="                
                sh "mvn -f greetings-app/pom.xml clean package -Dsurefire.skip=true sonar:sonar -Dsonar.host.url=http://localhost:9000 -Dsonar.projectName=pipeline-jenkins-vagrant-ansible-app -Dsonar.projectVersion=$BUILD_NUMBER";
            }           
        }






    }
}