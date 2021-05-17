def remote = [:]
remote.name = 'test'
remote.host = '3.238.194.4'
remote.port = 22
remote.allowAnyHosts = true


pipeline {
agent any

   stages {
     stage('git clone') {
       steps {
           git branch: 'main', credentialsId: '5a22a18e-6011-429e-971f-9cb1d3b24d20', url: 'https://github.com/sayan556/ec2test.git'
         }
       }
     stage('deployment') {
       steps {
          script {
           withCredentials([usernamePassword(credentialsId: 'ec2sshcred', passwordVariable: 'password', usernameVariable: 'username')]) {
    // some block

               remote.user = username
               remote.password = password
               sshPut remote : remote, from: "index.html" , into: "/var/www/html"
            }
          }
        }
     }
   }
}
