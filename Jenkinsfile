pipeline {
  agent {
    docker {
      args '-v /var/run/docker.sock:/var/run/docker.sock -p 127.0.0.1:1234:1234 TCP-LISTEN:1234,fork UNIX-CONNECT:/var/run/docker.sock'
      image 'bobrik/socat'
    }

  }
  stages {
    stage('Build1') {
      steps {
        sh 'docker run python:2-alpine'
      }
    }
    stage('build2') {
      steps {
        sh 'python -m py_compile sources/add2vals.py sources/calc.py'
      }
    }
  }
}