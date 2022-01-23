# crunchydb-ocp4
Repo for hosting CrunchyDB on OCP4. 


# Login / Switch to Primary Openshift Cluster
oc config use-context aws-0

# Installing Crunchydata Operator
oc apply -k install-operator/


```
namespace/postgres-operator created
customresourcedefinition.apiextensions.k8s.io/postgresclusters.postgres-operator.crunchydata.com configured
serviceaccount/pgo created
clusterrole.rbac.authorization.k8s.io/postgres-operator unchanged
clusterrolebinding.rbac.authorization.k8s.io/postgres-operator unchanged
deployment.apps/pgo created
pkthakur@Praveens-MacBook-Pro crunchydb-ocp4 %
```

oc apply -k primary-s3/

secret/pgo-s3-creds created
postgrescluster.postgres-operator.crunchydata.com/standby-s3 created


# Deploy the Postgres Standby Cluster 

# Login / Switch to Secondary Openshift Cluster

oc config use-context aws-1

oc apply -k install-operator/

```
namespace/postgres-operator created
Warning: resource customresourcedefinitions/postgresclusters.postgres-operator.crunchydata.com is missing the kubectl.kubernetes.io/last-applied-configuration annotation which is required by oc apply. oc apply should only be used on resources created declaratively by either oc create --save-config or oc apply. The missing annotation will be patched automatically.
customresourcedefinition.apiextensions.k8s.io/postgresclusters.postgres-operator.crunchydata.com configured
serviceaccount/pgo created
clusterrole.rbac.authorization.k8s.io/postgres-operator unchanged
clusterrolebinding.rbac.authorization.k8s.io/postgres-operator unchanged
deployment.apps/pgo created
```

oc apply -k standby-s3

```
secret/pgo-s3-creds created
postgrescluster.postgres-operator.crunchydata.com/standby-pg created
```

