# jenkins-master-slave-k8s

This is a PoC for a Kubernetes stack running in Minikube the following:

* Jenkins Master (default namespace)
* Jenkins Slave (jenkins-nodes namespace)

Basically this is a single Master using the kubernetes plugin spawning Slave nodes on request whenever a new job gets built.

The jenkins master needs some manual configuration, as in the example below.


## Installation

This is pretty straigh-forward.

You need to first build the custom Docker Image and after to create/apply the Kubernetes resources.

I am using the LATEST jenkins image what means things can change in the near future and this code might stop working.

Feel free to customize the Dockerfile file with any other plugins and dependencies of your liking.

So just do: 

```
docker build -t my-jenkins-image:1.0 .
kubectl apply -f cluster-role.yaml
kubectl apply -f jenkins-deployment.yaml
kubectl apply -f jenkins-service.yaml
```

