node{
    
    echo "Job Name is: ${env.JOB_NAME}" 
    echo "Build Number is: ${env.BUILD_NUMBER}" 
    echo "Node Name: ${env.NODE_NAME}" 
    echo "Jenkins Home Directory is: ${env.JENKINS_HOME}"  
    
    
    properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), [$class: 'JobLocalConfiguration', changeReasonComment: ''], pipelineTriggers([pollSCM('* * * * *')])])
    
    def mavenHome = tool name: '3.8.7'
    
    stage('CheckOutCode'){
        git branch: 'development', credentialsId: 'b32a8a8a-711a-4f7b-9eb7-65b03bf669ed', url: 'https://github.com/vurlugondajaydev/maven-web-application.git'
    }
    
    stage('Build'){
        sh "${mavenHome}/bin/mvn clean package"
    }
    /*
    stage('ExecuteSonarQubeReport'){
        sh "${mavenHome}/bin/mvn sonar:sonar"
    }
    
    stage('UploadArtifactsIntoNexus'){
        sh "${mavenHome}/bin/mvn clean deploy"
    }
    
    stage('DeployApplicationIntoTomcatServer'){
        sshagent(['60ea0573-3fb0-46c9-8cfd-e20318101189']) {
           sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@172.31.11.156:/opt/apache-tomcat-9.0.70/webapps/"    
        }
    }
    */
    
}
