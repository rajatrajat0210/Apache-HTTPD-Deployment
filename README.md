# Apache HTTPD Local Website Deployment
![image alt](https://github.com/rajatrajat0210/Apache-HTTPD-Deployment/blob/main/deployedwebsite.png?raw=true)
![image alt](https://github.com/rajatrajat0210/Apache-HTTPD-Deployment/blob/main/apache-vms.png?raw=true)

📌 Project Overview

This project sets up a local web server using Apache HTTPD on a CentOS virtual machine running on macOS (M2). The goal is to locally host an HTML website template from Tooplate.

🖥️ System Configuration

Host Machine: macOS (M2)

Virtual Machine: CentOS (Linux)

Allocated Resources:

🏗 RAM: 1600MB

⚙️ CPU: 2 Cores

🚀 Installation & Setup


1️⃣ Install Apache HTTPD
```bash
sudo yum install -y httpd
```

2️⃣ Enable and Start Apache Service
```bash
sudo systemctl enable httpd
sudo systemctl start httpd
```

3️⃣ Configure Firewall (Allow HTTP/HTTPS Traffic)
```bash
sudo firewall-cmd --permanent --add-service=http
sudo firewall-cmd --permanent --add-service=https
sudo firewall-cmd --reload
```

4️⃣ Download and Deploy Website Template
```bash
cd /tmp
wget https://www.tooplate.com/zip-templates/2137_barista_cafe.zip
unzip 2137_barista_cafe.zip
sudo cp -r 2137_barista_cafe/* /var/www/html/
```

5️⃣ Set Correct Permissions
```bash
sudo chown -R apache:apache /var/www/html/
sudo chmod -R 755 /var/www/html/
```

6️⃣ Restart Apache
```bash
sudo systemctl restart httpd
```

🌐 Accessing the Website

Open a browser and visit: http://<your_vm_ip>

Find your VM IP using:
```bash
ip addr show | grep inet
```
🛠 Troubleshooting

Check Apache status:
```bash
sudo systemctl status httpd
```
Verify firewall rules:
```bash
sudo firewall-cmd --list-all
```
Check logs for errors:
```bash
sudo journalctl -xe
sudo tail -f /var/log/httpd/access_log
sudo tail -f /var/log/httpd/error_log
```
📌 Future Enhancements

🔐 Add HTTPS with a self-signed SSL certificate.

🌍 Set up a custom domain with local DNS configuration.

🤖 Automate deployment using Ansible or a shell script. 
You can use VagrantFileIAC for automated proviosing of the website. 
Then just vist the http to make sure its working

📅 Project Details

Author: Rajat

Date: March 3, 2025

Purpose: Learning and experimenting with Apache HTTPD web hosting

🚀 Happy Hosting! 🎉
