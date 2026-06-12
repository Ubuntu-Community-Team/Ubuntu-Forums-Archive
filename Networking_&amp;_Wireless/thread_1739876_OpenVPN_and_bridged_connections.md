---
title: "OpenVPN and bridged connections"
date: 2011-04-26
forum: Networking &amp; Wireless
---

### Post by shopgeek on 2011-04-26
Goodmorning,

Recently I hacked together a router using some old hardware, two NICs and 10.04 LTS.

eth0 (wan port) is configured as a static inet using the data supplied by my ISP.  

eth1 (local) is configured as a static inet device (172.16.2.1), which is connected with the main switch / private network.

I used Firestarter for iptables / dhcpd configuration.  My mixed bag of clients (Win/Mac/Linux) obtain IPs and carry on with their tasks.

The requirement for road warriors to connect to the network has recently come up, so I thought I would take a stab at installing OpenVPN.  I followed some of the Ubuntu tutorials on how to set it up, which usually turned the router into a great stand-alone PC, until I undid everything.

I understand from my reading that a bridged connection is the way to go for OpenVPN.  My question is, what am I bridging?  Am I creating a 'tun0' device using openvpn and then bridging 'eth1' to 'tun0' as 'br0'?  After wrestling with it yesterday, I thought I would ask the experts.

Thank you.

---

### Post by shopgeek on 2011-04-26
Never mind.  After piecing together 4 or 5 different tutorials, I answered my own question.  I'll be putting together a how-to for those as new to this as I am....

---

