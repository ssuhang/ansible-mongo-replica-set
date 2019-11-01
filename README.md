Deployment of a mongodb replicaseth 
-----------------------------------------------------

This playbook setup a MongoDB replicaset with

Inventory
---------

The inventory/ENVIRONMENT.ini file defines the hosts (primary and secondaries) used for the replicaset.  
On top the host decalration, some databasqe parameters are defined

```
[primary]
PRIMARY_PUBLIC_IP

[primary_private]
PRIMARY_PRIVATE_IP

[secondary]
SECONDARY_1_PUBLIC_IP
SECONDARY_2_PUBLIC_IP

[secondary_private]
SECONDARY_1_PRIVATE_IP
SECONDARY_2_PRIVATE_IP

[primary:vars]
db_user_admin_username=USER_ADMIN_USERNAME
db_user_admin_password=USER_ADMIN_PASSWORD
db_cluster_admin_username=CLUSTER_ADMIN_USERNAME
db_cluster_admin_password=CLUSTER_ADMIN_PASSWORD
db_user_name=DB_USERNAME
db_user_password=DB_PASSWORD
db_name=DB_NAME
```

Nodes initialisation
--------------------

```ansible-playbook -i inventory/environment.ini main.yml --key-file=tony.pem --extra-vars '{"replSet":"replicasetname", "storage":"wiredtiger"}'```

If you want to cleanup everything

```ansible-playbook -i inventory/environment.ini clean.yml --key-file=tony.pem```
