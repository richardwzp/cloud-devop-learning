# kubernetes learning
This documents contain the notes I took while learning what kubernete is, which are gathered from a variety of sources. For accurate reference please go to the the official [kubernete documentation](https://kubernetes.io/docs/home/).


## Overview
A kubernete cluster can contain many nodes, each node could contain many pods, and each pod can contain many containers. 

### kubernete node
A node can be a virtual or a physical machine, depending how the cluster is set up. Typically in the node, you would have a [kubelet](#kubelet), a container runtime, and a kube-proxy.

***master node*** --- This runs the kubernete control plane which controls everything. It's the Kingpin of the entire kubernete cluster. There must be at least one of these in a given cluster, more is possible for redundency. The master node will include an API Server, etcd (a database that holds the state of the cluster), Controller Manager, and Scheduler.

***worker node*** --- These are the nodes that do the actual workload. They each have a [kubelet](#kubelet) inside.

### kubernete controller
The controller interact with the kubernete API server, to create/remove pods. 
The controller will attempt to bring the state toward your desired state, however it doesn't do the job for you.


### kubelet
This is an agent program that runs on each node. It's an intermidate between the node and the kubernete control plane (sort of like the big boss). It routinely does things like health check of its containers, gets the list of pods it need to run from the control plane, and reports the information back to the control plane.
Basically, if anyone wants to talk to the node, they must talk to the kubelet first.
