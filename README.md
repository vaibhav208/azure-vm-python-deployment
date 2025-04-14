# Cloud Infrastructure & Deployment (Azure VM + Python)

This project demonstrates how to deploy a simple Python (Flask) web application on an Azure Virtual Machine using the Azure GUI.

---

## 🧱 Architecture Diagram

```
                +--------------------------+
                |     User's Browser       |
                +-----------+--------------+
                            |
                            v
                +-----------+--------------+
                |    Azure Public IP        |
                | (Assigned to Virtual NIC) |
                +-----------+--------------+
                            |
                            v
                +-----------+--------------+
                |   Azure Virtual Machine   |
                |   Ubuntu Server (e.g.)    |
                | - Python + Flask App      |
                +--------------------------+
```

---

## ⚙️ Deployment Steps

### 1. Azure Resource Group & VM Creation
- Go to Azure Portal
- Create a **Resource Group** (e.g., `devops-assignment-rg`)
- Create a **Virtual Machine**
  - Image: Ubuntu 24.04 LTS
  - Size: Standard B1s
  - Inbound ports: HTTP (80), SSH (22)

### 2. SSH into the VM
```bash
ssh azureuser@<VM_PUBLIC_IP>
```

### 3. Install Python & Setup Flask App
```bash
sudo apt update
sudo apt install python3-venv -y
python3 -m venv venv
source venv/bin/activate
pip install flask
```

### 4. Create `app.py`
```python
from flask import Flask
app = Flask(__name__)

@app.route('/')
def home():
    return "Hello from Azure VM!"

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=80)
```

### 5. Run Flask App
```bash
sudo venv/bin/python app.py
```

Visit: `http://<VM_PUBLIC_IP>:80` in your browser.

---

## 🌐 Azure Configuration Summary

| Configuration        | Value                    |
|----------------------|--------------------------|
| Resource Group       | devops-assignment-rg     |
| VM Size              | Standard B1s             |
| OS Image             | Ubuntu 24.04 LTS         |
| Inbound Ports        | HTTP (80), SSH (22)      |
| Public IP            | Enabled                  |
| Flask Port           | 80                       |

---

## 📸 Screenshots

Include the following screenshots in the repository:
1. Azure VM Overview page
2. Flask app running in terminal
3. App response in browser

---


## 📬 Submission Info

This is part of the LiaPlus AI DevOps Internship assignment.  
Deployed using Azure GUI + Flask on VM.
