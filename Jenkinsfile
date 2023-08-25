node{
   stage('SCM Checkout'){
     git 'https://github.com/priya0010/my-app.git'
   }
   stage('Compile-Package'){

      def mvnHome =  tool name: 'maven', type: 'maven'   
      sh "${mvnHome}/bin/mvn clean package"
	  sh 'mv target/myweb*.war target/newapp.war'
   }
   stage('Build Docker Imager'){
   sh 'docker build -t said/myweb:0.0.2 .'
   }
   stage('Docker Image Push'){
   withCredentials([string(credentialsId: 'dockerPass', variable: 'dockerPassword')]) {
   sh "docker login -u priyad10 -p ${dockerPassword}"
    }
   sh 'docker push saidamo/myweb:0.0.2'
   }
   }
