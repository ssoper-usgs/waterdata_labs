pipeline {
  agent {
    node {
      label 'project:any'
    }
  }
  parameters {
    choice(choices: ['development', 'staging', 'production'], description: 'deployment environment', name: 'DEPLOY_TIER')
  }
  stages {
    stage('Build') {
      agent {
        dockerfile {
          args '-build-arg BLAH=PIKACHU -u root:root -v "${WORKSPACE}":/src -e "HUGO_BASEURL=/labs.waterdata"'
          reuseNode true
        }
      }
      steps {
        sh "/src/entrypoint.sh build"
      }
    }
  }
}
