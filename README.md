# ArgoCD-Simple-Application Creatoin
This guide will walk you through the process of installing Argo CD on a Kubernetes cluster, logging in, and creating an application using Guestbook as an example.

## Installation

1. **Install Argo CD using manifests:**
   ```bash
   kubectl create namespace argocd
   kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
Verify installation:
Check the status of the pods in the Argo CD namespace:
bash
Copy code
kubectl get pods -n argocd
Login
Retrieve the initial admin password:

bash
Copy code
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
Access the Argo CD UI:

Port Forwarding:
bash
Copy code
kubectl port-forward svc/argocd-server -n argocd 8080:443
Open your browser and visit: https://localhost:8080
Create Application (Guestbook)
Go to the Argo CD UI:
Open your browser and access the Argo CD UI using the method from the previous section.

Create Application:

Click on "Create Application".
Provide a name, e.g., guestbook.
Specify the GitHub repository URL and the path to the application manifest, e.g., guestbook.
Provide the cluster URL, namespace, and any other required information.
Click on "Create" to deploy the application.
Verify Deployment:

Check the status of the deployment in the Argo CD UI.
Alternatively, you can use kubectl commands to verify:
bash
Copy code
kubectl get pods -n <namespace>
Congratulations! You have successfully installed Argo CD, logged in, and deployed an application using Guestbook.
