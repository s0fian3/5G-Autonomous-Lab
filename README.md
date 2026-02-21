# 5G Autonomous Lab: End-to-End Private 5G Core Deployment

This project demonstrates the automated deployment of a private 5G Core (Open5GS) and RAN simulator (UERANSIM) using Infrastructure as Code (Terraform) and Configuration Management (Ansible).

## 🛠️ Tech Stack
- **Orchestrator:** Kali Linux (Rolling)
- **Nodes:** Ubuntu 20.04 Focal (VirtualBox)
- **Automation:** Ansible Core 2.13.x
- **5G Core:** Open5GS
- **Database:** MongoDB
- **Simulated Radio:** UERANSIM

## 🚧 Challenges Overcome
### Python Dependency Resolution
- **Problem:** Modern Ansible on Kali required Python 3.9+, but target Ubuntu nodes utilized Python 3.8.
- **Solution:** Performed a targeted downgrade of Ansible-Core to 2.13 and utilized the `ansible_python_interpreter` flag to maintain system stability without risky OS upgrades.

### Multi-Homed Network Routing
- **Problem:** VMs lost internet access during provisioning due to NAT/Host-Only conflicts.
- **Solution:** Implemented a Bridged Adapter strategy and utilized `iproute2` for manual route injection to maintain both private signaling and public update paths.
