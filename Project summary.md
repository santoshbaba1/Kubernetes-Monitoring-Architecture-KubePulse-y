⚡ **KubePulse: Kubernetes Observability & Monitoring**
KubePulse is a lightweight, real-time observability and health-monitoring system deployed locally inside a Kind (Kubernetes-in-Docker) cluster. It provides a visual control center and a metrics pipeline to monitor cluster infrastructure, workloads, and alerts.

**Mermaid diagram**

<img width="459" height="445" alt="image" src="https://github.com/user-attachments/assets/eb21127d-2e76-4f8d-9391-4c612b995290" />

🛠️ **Key Architectural Components**


**1. Interactive Dashboard (Streamlit Frontend)**

Role: The user-facing control panel.
Features: Displays summary metrics (Node counts, namespaces, pod allocations), detailed lists of active Pods and Deployments (with namespace filters), Node infrastructure specifications, active Alertmanager warning cards, and a live Kubernetes event stream.
Design: Uses a clean, dark-mode glassmorphic interface and centers action buttons to open auxiliary monitoring tools.



**2. Control Center API (FastAPI Backend)**

Role: The bridge between the Kubernetes cluster and the user dashboard.
Features: Uses the official Kubernetes Python Client library to query the Kubernetes API Server. It exposes API endpoints (/api/cluster/summary, /pods, /nodes, etc.) and hosts a webhook endpoint (/api/alerts/webhook) that receives alerts from Alertmanager.



**3. Metric Pipeline (Prometheus)**

Role: Time-series database and metric aggregator.
Features: Configured to scrape metrics from the API Server, Kubernetes nodes (Kubelet), and container resource metrics (via cAdvisor).



**4. Visual Analytics (Grafana)**

Role: Visual graphing and dashboarding.
Features: Provisioned automatically with a default datasource and a custom KubePulse Monitoring Dashboard as its home page. It displays real-time timeseries graphs for:
CPU/Memory usage per pod
Total cluster capacity
Pod network throughput rates (TX/RX)



**5. Routing Gateway (NGINX Ingress)**

Role: Routes all traffic from your host machine into the Kind cluster container network.

**Pathing Rules:**
http://localhost/ 

**Streamlit Frontend UI**
http://localhost/api 

**FastAPI Backend API**
http://localhost/prometheus 

**Prometheus Web UI**
http://localhost/grafana 

**Grafana Analytics Dashboard**
