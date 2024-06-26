# Kubernetes Prometheus Monitoring Stack with DaemonSet

This repository contains Kubernetes YAML files to deploy the Prometheus monitoring stack on your Kubernetes cluster. The stack includes Prometheus server deployed via Deployment, Prometheus Node Exporter deployed via DaemonSet to monitor all nodes in the cluster, and Grafana for visualization purposes installed using HELM.

## Components

- **Prometheus Server**: The core component for gathering metrics from monitored targets by scraping metrics HTTP endpoints.
- **Prometheus Node Exporter**: Deployed as a DaemonSet, it collects hardware and kernel metrics from each node and exports them to Prometheus.
- **Grafana**: A powerful visualization tool used to create, explore, and share dashboards and data with your team.

## Prerequisites

Before deploying the monitoring stack, ensure the following prerequisites are met:

- Kubernetes cluster is up and running.
- `kubectl` is configured to access the Kubernetes cluster.
- HELM is installed for installing Grafana.

## Deployment

To deploy the monitoring stack, follow these steps:

1. Clone this repository:

    ```bash
    git clone https://github.com/yogendra-kokamkar/kubernetes-cluster-monitoring.git
    ```

2. Navigate to the repository directory:

    ```bash
    cd kubernetes-cluster-monitoring
    ```

3. Apply the Kubernetes YAML files:

    ```bash
    kubectl apply -f .
    ```

4. Install Grafana using HELM:

    ```bash
    helm install grafana stable/grafana
    ```

## Accessing Services

Once deployed, you can access the following services by port-forwarding them:

- **Prometheus Server**: Accessible at `http://your-public-ip:9090`.
  
  To port forward Prometheus:
  ```bash
  kubectl port-forward --address 0.0.0.0 service/prometheus 9090:80 -n prometheus
  ```
  ![2](https://github.com/yogendra-kokamkar/kubernetes-cluster-monitoring/assets/55878086/d907680a-ed13-4f3c-96dd-5b9e5e5fe949)

- **Node Exporter Server**: Accessible at `http://your-public-ip:9100`.

  To port forward Node Exporter:
  ```bash
  kubectl port-forward --address 0.0.0.0 service/node-exporter 9100:9100 -n prometheus
  ```
  ![3](https://github.com/yogendra-kokamkar/kubernetes-cluster-monitoring/assets/55878086/ce56322d-6b6b-4496-94ea-3459b040570c)
  ![4](https://github.com/yogendra-kokamkar/kubernetes-cluster-monitoring/assets/55878086/d2c482c3-3f7a-45ad-bbe1-26f58a3366a5)

 
- **Grafana Server**: Accessible at `http://your-public-ip:3000`.

  To port forward Grafane:
  ```bash
  kubectl port-forward --address 0.0.0.0 service/grafana 3000:80
  ```
  ![1](https://github.com/yogendra-kokamkar/kubernetes-cluster-monitoring/assets/55878086/2a46cba6-29d1-47a8-9975-7495b29b88ef)
## Contributing
Contributions to this repository are welcome! If you have suggestions, improvements, or additional content to add, please open an issue or submit a pull request.

## License
This project is licensed under the [MIT License](LICENSE).
