# sql-server-on-gke

## Create the Cluster

```bash
gcloud container clusters create kubernetes-cluster --project=your-project-id --zone=us-central1-a
```

## Connect to the Cluster

```bash
gcloud container clusters get-credentials kubeernetes-cluster --zone us-central1-a --project=your-project-id
```

## Create a password for sa

```bash
kubectl create secret generic mssql-secrets --from-literal=SA_PASSWORD="Super-secret-pa$$word-Here!"
```

## Create the disks and the deployment

```bash
kubectl apply -f volume-claims.yaml

kubectl apply -f mssql-deployment.yaml

kubectl apply -f mssql-service.yaml
```

### A load balancer running on port 1433 is created. Connect with your favorite tool
