properties([pipelineTriggers([githubPush()])])

node('linux') {
  stage('Setup'){
    sh 'aws s3 cp s3://seis665-03-asm10/classweb.html ./index.html'
  }
  stage('Build'){
    sh 'docker build -t classweb:1.0 .'
  }
  stage('Test'){
    sh 'docker run -d -p 80:80 --env NGINX_PORT="80" classweb:1.0'
    sh 'curl -s 10.120.1.196'
    }
  }
}
