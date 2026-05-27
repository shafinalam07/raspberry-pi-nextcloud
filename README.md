# 🏠 Self-Hosted Personal Cloud — Raspberry Pi + Nextcloud

A self-hosted cloud storage solution built on a Raspberry Pi 3B+
using Docker and Nextcloud. Your own private Google Drive —
no monthly fees, full data privacy, complete control.

![Nextcloud](https://img.shields.io/badge/Nextcloud-0082C9?style=for-the-badge&logo=nextcloud&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Raspberry Pi](https://img.shields.io/badge/Raspberry%20Pi-A22846?style=for-the-badge&logo=raspberrypi&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)

---

## 📌 Project Overview

This project turns a Raspberry Pi 3B+ into a fully functional
personal cloud server accessible from any device on the local network.
Built entirely from scratch with no prior Linux experience.

---

## 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| Raspberry Pi 3B+ | Hardware server |
| Raspberry Pi OS Lite | Operating system |
| Docker | Container runtime |
| Nextcloud | Cloud storage application |
| SSH | Remote access |
| WiFi Networking | Local network connectivity |

---

## 📋 Prerequisites

- Raspberry Pi 3B+ (or newer)
- MicroSD card (16GB minimum)
- Laptop with SSH client (PuTTY on Windows)
- Home WiFi network (2.4GHz)
- Raspberry Pi Imager

---

## 🚀 Setup Guide

### Step 1 — Flash Raspberry Pi OS

1. Download [Raspberry Pi Imager](https://raspberrypi.com/software)
2. Select device: Raspberry Pi 3
3. Select OS: Raspberry Pi OS Lite (32-bit)
4. Configure settings before flashing:
   - Enable SSH
   - Set username: `pi`
   - Set your password
   - Enter WiFi credentials (2.4GHz only)
   - Set WiFi country: `IN`
5. Flash to MicroSD card

### Step 2 — Boot and Connect

```bash
# Insert MicroSD into Pi and power on
# Wait 90 seconds, then SSH from laptop
ssh pi@raspberrypi.local

# Update the system
sudo apt update && sudo apt upgrade -y
```

### Step 3 — Install Docker

```bash
# Install Docker
sudo apt install -y docker.io

# Add pi user to docker group
sudo usermod -aG docker pi

# Reboot
sudo reboot
```

### Step 4 — Deploy Nextcloud

```bash
# Pull and run Nextcloud container
sudo docker run -d \
  -p 8080:80 \
  --name nextcloud \
  --restart always \
  nextcloud

# Verify container is running
sudo docker ps
```

### Step 5 — Access Nextcloud

Open browser and navigate to:
http://192.168.1.12:8080

Create admin account and complete setup.

---

## 📸 Screenshot

### Nextcloud Dashboard
<img width="1912" height="922" alt="image" src="https://github.com/user-attachments/assets/2f89f2c3-b52b-4272-9f52-5cf4dbf3db66" />


---

## 🔧 Troubleshooting

| Issue | Fix |
|---|---|
| Pi not on WiFi | Use 2.4GHz network, Pi 3B+ doesn't support 5GHz |
| SSH not connecting | Wait 90 seconds after boot, check IP with `arp -a` |
| Docker install fails | Use `sudo apt install docker.io` instead of get.docker.com script |
| Nextcloud crashes | Add swap memory to Pi |

---

## 📚 What I Learned

- Linux command line basics
- SSH remote access and server management
- Docker containerization
- Self-hosting web applications
- Network configuration and troubleshooting
- Raspberry Pi setup and configuration

---

## 🔮 Future Improvements

- [ ] Add swap memory for better stability
- [ ] Set up HTTPS with SSL certificate
- [ ] Configure external storage
- [ ] Enable remote access from outside home network
- [ ] Set up automated backups
- [ ] Migrate to MySQL database for better performance

---

## 👤 Author

- GitHub: [shafinalam07](https://github.com/shafinalam07)

---
