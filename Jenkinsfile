pipeline {
      agent any
      environment { 
		PATH= "/opt/maven/bin:$PATH"
      }
      stages {
	stage("bulid") {
	   steps {
             sh 'mvn clean deploy'
           }
        }
        stage('sonarqube analysis') { 
          environment {
                 scannerHome = tool 'saidemy-sonarqube-scnner'
          }
          steps {
              withSonarQubeEnv('saidemy-sonarqube-server') {
		 sh "${scannerHome}/bin/sonar-scanner"
                 }
           }
         }
       }
}
		
