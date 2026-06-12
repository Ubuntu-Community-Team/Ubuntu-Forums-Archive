---
title: "Ubuntu Server 11.04 NAT problems - port forwarding"
date: 2011-11-17
forum: Networking &amp; Wireless
---

### Post by salvor_hardin on 2011-11-17
Hello!

Ubuntu server 11.04 64bit with vmware workstation 8.0 installed with Win XP guest!

I'm trying to get RDP working to VM! I'm having problems with ports on Ubuntu. I used ufw to open port **3389 tcp** for incoming connections allow anywhere and **port 9997** allow from **192.168.157.0/24**. I configured forwarding in vmware NAT.conf for 9997 tcp to VM address.
What is strange to me is that when I run **netstat -lntup** as root these ports are nowhere to be shown. When I run ufw status they are shown as opened. Scanning Ubuntu using **Nmap** only shows **3389 tcp closed ms-term-serv**. Nmap should show at least few more ports as open!

I would appreciate if anybody would help me with this! 

Thank you!

---

### Post by salvor_hardin on 2011-11-18
Looks like ufw firewall, when enabled, blocks all traffic by default. But Nmap, when scanning Ubuntu server from another machine, lists 3389tcp and 9997tcp as closed but on Ubuntu ufw status shows tgat those ports are open.

---

