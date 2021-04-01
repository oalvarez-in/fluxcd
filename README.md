# Managing Helm releases with Fluxcd

## Architecture

---

<img src="https://docs.fluxcd.io/projects/helm-operator/en/stable/_files/fluxcd-helm-operator-diagram.png" width="650px" height="350px">

## Steps

---

> kubectl create namespace fluxcd

```
export GIT_USER=xxxxx
export GIT_TOKEN=xxxxxxxxx
export GIT_EMAIL=xxxx@xxxx.com

helm upgrade -i flux fluxcd/flux \
 --set git.url=https://$GIT_USER:$GIT_TOKEN@github.com/oalvarez-in/fluxcd.git \
--set git.email=GIT_EMAIL \
--set git.branch=main \
--set namespace=fluxcd \
--set git.path=fluxcd/releases/ \
--set git.user=$GIT_USER
```

```
helm upgrade -i helm-operator fluxcd/helm-operator --namespace fluxcd \
--set helm.versions=v3
```
