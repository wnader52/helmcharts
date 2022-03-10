# This is the installation file for redis cache deployment and service using helm3 charts.
## 1. Build and install redis-app 
    helm create redis
### a. Copy redis-deployment.yaml and redis-service.yaml into templates/
### b. Create variables in values.yaml and update Chart.yaml (description)
### c. Update redis-deployment.yaml and redis-service.yaml files with variables
### d. ```helm template ./redis``` (see how the deployment in yaml looks like)
      helm template ./redis
### e. ```helm lint ./redis``` (check schema of redis app)
      helm lint ./redis
### f. Fix any errors and run ```helm lint ./redis``` again until errors are clear
### g. cd to ```../redis```
### h. ```helm install my-redis-release ./redis``` (to install redis deployment/service/volume)
       helm install my-redis-release ./redis
### i. ```helm list -a``` (list out your helm installations)
      helm list -a
### j. ```kubectl get all``` (see deployment, service, pod and volume - see my-redis-release)
      kubectl get all
### k. ```helm delete <my-redis-release>``` (This will delete the installation of redis from the helm list command)
      helm delete <my-redis-release>

### l. ```kubectl get all``` (Check to make sure services are running like below:) 
      service/my-redis-release          NodePort    10.109.86.51     <none>        80:30884/TCP     11m
      deployment.apps/my-redis-release             1/1     1            1           11m
      pod/my-redis-release-75f88f84c8-clzzt             1/1     Running   0               11m

## 2. Test your deployment of redis-app using helm3.
### a. kubectl get pods (get the redis pod)
### b. kubectl  exec -it <redis-deployment-5d8c696577-rm5p4> -- bash (get into the pod and check redis-cli)
### c. root@redis-deployment-5d8c696577-rm5p4:/data# redis-cli (redis-cli)
### d. 127.0.0.1:6379> ping (should give PONG)
### e. 127.0.0.1:6379> set key1 "value1"
### f. 127.0.0.1:6379> get key1 (should print "value1")
### g. 127.0.0.1:6379> set key1
### h. 127.0.0.1:6379> exit (exit from redis-cli)
### i. root@redis-deployment-5d8c696577-rm5p4:/data# exit (exit from pod)