# KUBERNETES - K8S

## CRIAR CLUSTER KUBERNETES
=========================================
#### install [docker](https://desktop.docker.com/win/stable/amd64/Docker%20Desktop%20Installer.exe) on windows

#### install k3d on windows

```sh
choco install k3d
```
##### install kubectl on windows
```sh
choco install kubernetes-cli
```

#### Criar cluster test
```sh
k3d cluster create mycluster-1node
```

#### Connect to cluster created
Para mostrar:
```sh
kubectl config view
```

Para selecionar:
```sh
kubectl config use-context k3d-mycluster-1node
```
Switched to context "k3d-mycluster-1node".

Para verificar:
```sh
kubectl.exe get nodes
```
NAME                           STATUS   ROLES                  AGE   VERSION
k3d-mycluster-1node-server-0   Ready    control-plane,master   15m   v1.21.1+k3s1

#### List clusters k3d
```sh
k3d cluster list
```

#### delete cluster k3d
```sh
k3d cluster delete mycluster-1node
```

#### Criar cluster 
```sh
k3d cluster create mycluster --servers 1 --agents 2
```

## Comands and Concepts K8S

- **1-Concepts**
Garantir escalabilidade com replicaset

- **2-Commands**
Manifests: Name, kind and version
```sh
kubectl.exe api-resources
```

Labels
```sh
kubectl.exe get pods -l app=nginx
NAME            READY   STATUS    RESTARTS   AGE
my-second-app   1/1     Running   0          5s

kubectl.exe get pods -l name=my-first-app
NAME           READY   STATUS    RESTARTS   AGE
my-first-app   1/1     Running   0          5m6s
```

Port Forward
```sh
kubectl.exe port-forward pod/my-first-replicaset-hpz9v 8000:80
Forwarding from 127.0.0.1:8000 -> 80
Forwarding from [::1]:8000 -> 80
Handling connection for 8000
Handling connection for 8000
```

Roolback
```sh
kubectl.exe rollout undo deployment my-first-deployment
```