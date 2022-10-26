# Run a Helm Chart per VCluster

## Install VCluster

### Install the VCluster CLI

```
curl -L -o vcluster "https://github.com/loft-sh/vcluster/releases/latest/download/vcluster-linux-amd64" && sudo install -c -m 0755 vcluster /usr/local/bin
```

### Start minikube

```
minikube start
```

### Create a virtual cluster using the `vcluster` CLI.

```
vcluster create helm-poc
```

A namespace called `vluster-helm-poc` will be created on minikube. Once the vcluster is up your kubecontext will change to the vcluster.

If you run the following command you can see that a new context has been created with the name `vcluster_helm-poc_vcluster-helm-poc_minikube`

```
kubectl config get-clusters
```

## Install a Helm chart on the VCluster

Now that you are already in the VCluster you can install a helm chart with the following command.

```
helm repo add bitnami https://charts.bitnami.com/bitnami
helm install bitnami/mysql --generate-name
```



