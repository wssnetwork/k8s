# CKA Certification Module

## Storage
* Ref https://kubernetes.io/docs/concepts/storage/

### Understand storage classes, persistent volumes
* ConfigMap - to map with configuration files to the pods https://kubernetes.io/docs/tasks/configure-pod-container/configure-pod-configmap/

* Persistent volumes - https://kubernetes.io/docs/concepts/storage/persistent-volumes/

    * Sample walkthrough https://kubernetes.io/docs/tasks/configure-pod-container/configure-persistent-volume-storage/
    * Persistent volume will map to physical storage directory (on server)
    * Persistent volume claim is requesting from persistent volume
    * Pod will declare the pv and pvc, together mount in pod volume

### Understand volume mode, access modes and reclaim policies for volumes
* Volume mode - https://kubernetes.io/docs/concepts/storage/persistent-volumes/#volume-mode

    * volumeMode: Filesystem - default mode. the common in linux filesystem.
    * volumeMode: Block - the raw block storage. app must know how to handle the raw block storage.

* Access mode - https://kubernetes.io/docs/concepts/storage/persistent-volumes/#access-modes

    * ReadWriteOnce - the volume can be mounted as read-write by a single node. ReadWriteOnce access mode still can allow multiple pods to access the volume when the pods are running on the same node.
    * ReadOnlyMany - the volume can be mounted as read-only by many nodes.
    * ReadWriteMany - the volume can be mounted as read-write by many nodes.
    * ReadWriteOncePod - the volume can be mounted as read-write by a single Pod. only one pod across whole cluster can read that PVC or write to it. This is only supported for CSI volumes and Kubernetes version 1.22+.

* Reclaim policies - https://kubernetes.io/docs/concepts/storage/persistent-volumes/#reclaim-policy

    * Retain - manual reclamation. if PV is delete, local file in storage still remain.
    * Recycle - basic scrub (rm -rf /thevolume/*)
    * Delete - associated storage asset such as AWS EBS, GCE PD, Azure Disk, or OpenStack Cinder volume is deleted
    * Currently, only NFS and HostPath support recycling. AWS EBS, GCE PD, Azure Disk, and Cinder volumes support deletion.

### Understand persistent volume claims primitive
### Know how to configure applications with persistent storage

## Troubleshooting
Evaluate cluster and node logging
Understand how to monitor applications
Manage container stdout & stderr logs
Troubleshoot application failure
Troubleshoot cluster component failure
Troubleshoot networking

## Workloads & Scheduling
Understand deployments and how to perform rolling update and rollbacks
Use ConfigMaps and Secrets to configure applications
Know how to scale applications
Understand the primitives used to create robust, self-healing, application deployments
Understand how resource limits can affect Pod scheduling
Awareness of manifest management and common templating tools

## Cluster Architecture, Installation & Configuration
Manage role based access control (RBAC)
Use Kubeadm to install a basic cluster
Manage a highly-available Kubernetes cluster
Provision underlying infrastructure to deploy a Kubernetes cluster
Perform a version upgrade on a Kubernetes cluster using Kubeadm
Implement etcd backup and restore

## Services & Networking
Understand host networking configuration on the cluster nodes
Understand connectivity between Pods
Understand ClusterIP, NodePort, LoadBalancer service types and endpoints
Know how to use Ingress controllers and Ingress resources
Know how to configure and use CoreDNS
Choose an appropriate container network interface plugin