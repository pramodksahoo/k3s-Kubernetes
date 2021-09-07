## K3s - Lightweight Kubernetes
===============================================

`Install Lightweight Kubernetes in a single Node`

`Production ready, easy to install`


## Quick-Start - Install Script

The `install.sh` script provides a convenient way to download K3s and add a service to systemd or openrc.

To install k3s as a service just run:

```bash
curl -sfL https://get.k3s.io | sh -
```
# Single Command for installation with specific version

```bash
curl -sfL https://get.k3s.io | INSTALL_K3S_VERSION="v1.21.3+k3s1" sh -s -
```

# Single Command for installation with specific version & exclude services like traefik, servicelb

```bash
curl -sfL https://get.k3s.io | INSTALL_K3S_VERSION="v1.21.3+k3s1" INSTALL_K3S_EXEC="--no-deploy servicelb" INSTALL_K3S_EXEC="--no-deploy traefik" sh -s -
```

A kubeconfig file is written to `/etc/rancher/k3s/k3s.yaml` and the service is automatically started or restarted.
The install script will install K3s and additional utilities, such as `kubectl`, `crictl`, `k3s-killall.sh`, and `k3s-uninstall.sh`, for example:

```bash
k3s kubectl get nodes
```
Check pods are running:
```bash
k3s kubectl get pods -A
```

`K3S_TOKEN` is created at `/var/lib/rancher/k3s/server/node-token` on your server.
To install on worker nodes we should pass `K3S_URL` along with
`K3S_TOKEN` or `K3S_CLUSTER_SECRET` environment variables, for example:

```bash
curl -sfL https://get.k3s.io | K3S_URL=https://myserver:6443 K3S_TOKEN=XXX sh -
```


