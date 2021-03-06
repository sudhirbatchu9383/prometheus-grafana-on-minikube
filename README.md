# Prometheus and Grafana on Minikube

## Setup 

1. Install kubectl (https://kubernetes.io/docs/tasks/tools/install-kubectl/)
  * On MacOs: `brew install kubectl`

2. Install minikube ([https://github.com/kubernetes/minikube]()).
  * On MacOs `brew cask install minikube`

3. Add aliases to /ect/hosts for simple access:
  * Determine actual ip with `minikube ip`

```
192.168.99.100  minikube.local prometheus.local alertmanager.local grafana.local
```

4. Install helm ([https://docs.helm.sh/using_helm/#installing-helm]())
  * On MacOs `brew install kubernetes-helm`
  * Install helm on the minikube: `helm init`

5. Install/Deploy Prometheus on Minikube:
  * `helm install -n monitoring -f prometheus/values.yaml stable/prometheus`
After Deployment is done, Prometheus UI can be accessed at [http://prometheus.local]() and Alertmanager UI at [http://alertmanager.local]().


6. Install Grafana ([https://grafana.com/grafana]())
  * `helm install -n grafana -f grafana/values.yaml stable/grafana`
After Deployment is done Grafana UI can be accessed at [http://grafana.local](). Use User `admin` and the password `admin`.

Prometheus is configured as default datasource. 

There is already a preinstalled dashboard: "Kubernetes cluster monitoring (via Prometheus)".





### Some helpful Notes:
Force reload of prometheus config:
`curl -X POST http://prometheus.local/-/reload`

