## Kubectl Commands

#### Here are some of the most useful kubectl commands. This is a living list so feel free to suggest commands you find useful. 

##### Get pods sorted by creation time
`kubectl get pods --sort-by .metadata.creationTimestamp`


##### Create a simple pod for trouble shooting
Create a base Debian pod that we can install our tools onto.

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: debian
  namespace: default
spec:
  containers:
  - name: debiantest
    image: debian:latest
    command:
      - sleep
      - "3600"
    imagePullPolicy: IfNotPresent
  restartPolicy: Always
```

To create the container run the following command.
```
kubectl create -f https://raw.githubusercontent.com/patrickbeam/useful-kubectl-commands/master/debiantest.yaml
```
```
pod/debian created

kubectl get pods debian -n default
NAME     READY   STATUS    RESTARTS   AGE
debian   1/1     Running   0          25s
```

### Kubespy
https://github.com/pulumi/kubespy
- kubespy is a small tool that makes it easy to observe how Kubernetes resources change in real time
- `brew install kubespy`

