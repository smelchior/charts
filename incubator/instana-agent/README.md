# Helm Chart for Instana Kubernetes

This is a helm chart for deploying the Instana agent to a Kubernetes cluster.

### Prerequisites

To use this, first install `helm` and tiller (the Kubernetes cluster-side tool helm talks to) using the standard documentation:

[https://docs.helm.sh/using_helm/#installing-helm](https://docs.helm.sh/using_helm/#installing-helm)

Install tiller to your cluster with `helm init`
### Running

Once helm is installed and `helm list` works (probably only shows an empty list at this point), you can install the agent via the chart:

```
helm install . --name instana-agent --namespace instana-agent --set instana.agent.key=your-key --set instana.zone=cluster-name
```

The output of this command should be something like the following:

```
NAME:   instana-agent
LAST DEPLOYED: Fri Jan 26 11:22:32 2018
NAMESPACE: instana-agent
STATUS: DEPLOYED

RESOURCES:
==> v1/ClusterRole
NAME                  AGE
instana-agent-reader  0s

==> v1/ClusterRoleBinding
NAME                          AGE
instana-agent-reader-binding  0s

==> v1beta1/DaemonSet
NAME           DESIRED  CURRENT  READY  UP-TO-DATE  AVAILABLE  NODE SELECTOR  AGE
instana-agent  4        4        0      4           0          <none>         0s

==> v1/Pod(related)
NAME                 READY  STATUS             RESTARTS  AGE
instana-agent-5p5zc  0/1    ContainerCreating  0         0s
instana-agent-dnzq4  0/1    ContainerCreating  0         0s
instana-agent-f7sls  0/1    ContainerCreating  0         0s
instana-agent-ldhvs  0/1    ContainerCreating  0         0s

==> v1/Secret
NAME                  TYPE    DATA  AGE
instana-agent-secret  Opaque  1     0s

==> v1/ServiceAccount
NAME           SECRETS  AGE
instana-agent  1        0s
```
