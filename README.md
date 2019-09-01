# learn-go-k8s 
Learn building a sample Go applicaton in Kubernetes

## Getting Started
First, clone the repo via git:
```
$ git clone https://github.com/rickhysis/learn-go-k8s.git
```

## Dockerizing the Go application
```
# Build the docker image
$ docker build -t learn-go-k8s .
# Tag the image
$ docker tag learn-go-k8s rickhysiswanto/learn-go-k8s:1.0.0
```

## Starting a local Kubernetes cluster using Minikube and deploying the app
You’ll need to install and set up kubectl (Kubernetes command-line tool) and Minikube to proceed further. Please follow the instructions on the official Kubernetes website to install kubectl and minikube.

Once the installation is complete, type the following command to start a Kubernetes cluster:
```
$ minikube start
```

Let’s now deploy our app to the minikube cluster by applying the deployment manifest using kubectl.
```
$ kubectl apply -f k8s/deployment.yml
# and then You can type the following command to get the pods in the cluster
$ kubectl get pods
NAME                            READY   STATUS    RESTARTS   AGE
learn-go-k8s-6667d94cdc-cpfhd   1/1     Running   0          28s
learn-go-k8s-6667d94cdc-cqltm   1/1     Running   0          28s
learn-go-k8s-6667d94cdc-qb2w4   1/1     Running   0          28s
```

## Scaling a Kubernetes deployment
You can scale the number of Pods by increasing the number of replicas in the kubernetes 
```
$ kubectl scale --replicas={number} deployment/learn-go-k8s
```