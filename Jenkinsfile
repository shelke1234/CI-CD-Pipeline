pipeline {  
    agent any  
    stages {  
            stage ('Git-Checkout') {  
                steps{
                    git credentialsId: 'git', url: 'https://github.com/shelke1234/CI-CD-Pipeline.git'
                    echo "Checkout successful";
                } 
            }
            stage ('Compile') {  
                  steps{
                    sh: 'mvn compile'
                    echo "test successful";
                    
                } 
            }
            stage ('Build') {  
                  steps{
                    sh: 'mvn clean'
                    sh: 'mvn package'
                    echo "build successful";
                    
                } 
            }
             stage ('Test') {  
                  steps{
                     sh:'mvn test'
                    echo "test successful";
                } 
            }
            
     
        }
    }
}

 stage ('Deploy') {
            steps{
            deploy adapters: [tomcat9(credentialsId: 'dhananjay', path: '', url: 'http://15.206.70.50:8080/')], contextPath: 'jenkins_calci', onFailure: false, war: '**/*.war'
             echo "Deploy successful";
            }
        }
        stage ('Monitor') { 
           steps{ 
             echo "Now you can monitor!";
           }
        }
    }
}
