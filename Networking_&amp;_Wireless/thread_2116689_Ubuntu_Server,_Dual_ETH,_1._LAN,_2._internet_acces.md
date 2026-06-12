---
title: "Ubuntu Server, Dual ETH, 1. LAN, 2. internet access"
date: 2013-02-16
forum: Networking &amp; Wireless
---

### Post by Vaseer on 2013-02-16
I am setting up Home Server on Ubuntu Server 12.04. I would like set up two separated ETH connections on Server.
1st (eth0): for local access:  local devices <-> Server
2nd (eth1): for Server’s internet access (only for uTorrent) – PPPoE connection

eth0 on Server will be connected to local router, which has also PPPoE connection – on router are connected all local devices (at the same time, I can establish 2 PPPoE connections). 
I would like to set up:
- eth0 only for local access and block all internet connections
- eth1 only for uTorrent internet access and block all other internet traffic

Server ETH configuration:
LAN:
eth0 – RJ45 connector on motherboard (1Gb/s) <-> connected to router
IP: 192.168.20.10
Gateway: 192.168.20.1
Subnet mask: 255.255.255.0

Internet access (server only!):
eth1 – USB to ETH adapter (100Mb/s) <-> connected to modem
IP: 192.168.1.10
Gateway: 192.168.1.1
Subnet mask: 255.255.255.0

Need help configuring…

Do you have any suggestions on USB to ETH adapter?

Vaseer

---

### Post by Vaseer on 2013-02-17
Any advice?

---

