# minikube-aws

This is the project for Minikube execution environment.

The maintaner uses EC2 instance(Amazon Linux2) as the virtual machine.

Minikube need 2CPUs, so the instance type is larger than t2.medium.

## Setup
SSH to EC2 Instance and follow these steps in it.

### Git
```
$ sudo yum update
$ sudo yum install -y git
$ mkdir ~/workspace
$ cd workspace
$ git clone https://github.com/takahiroaoki/minikube-aws.git
```

### Docker & Minikube
```
$ cd ~/workspace/minikube-env
$ make init
```

## How to use
```
$ minikube start
$ kubectl apply -f nginx/nginx.yml

# After the following, you can access http://localhost:8080
$ kubectl port-forward service/${service name} 8080:${load balancer's port}
```

## Appendix
### minikube
```
# start node
$ minikube start

# stop node
$ minikube stop

# check status
$ minikube status

# delete node
$ minikube delete

# check addons
$ minikube addons list
```

### kubectl
```
# apply manifest file
$ kubectl apply -f ${file name}

# delete resource
$ kubectl delete -f ${file name}

# check pod status
$ kubectl get pod [-o wide]

# connect to pod
$ kubectl exec -it ${pod name} -- sh

# copy file to pod
$ kubectl cp ${src path} ${pod name}:${dest path}

# copy file from pod
$ kubectl cp ${pod name}:${src path} ${dest path}

# check pod info
$ kubectl describe pod/${pod name}

# check log in a pod
$ kubectl logs pod/${pod name}
```
