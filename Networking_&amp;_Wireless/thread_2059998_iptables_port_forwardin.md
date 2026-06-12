---
title: "iptables port forwardin"
date: 2012-09-19
forum: Networking &amp; Wireless
---

### Post by soad18 on 2012-09-19
I'm having problems setting up port forwarding for PPTP on a Linux machine to a W2003 VP-server.
On linux machine i have eth0 with static ip and internet acces and eth1 for Lan 10.8.1.1/24 

I'm running Ubuntu 10.4 with a 2.6.32 Kernel with this nat setting:
 -A POSTROUTING -s 10.8.1.1/24 -j SNAT --to-source $StaticIP
My setup to forwading trafic for port 1723 to deseire ip is:

-A PREROUTING -i eth0 -p tcp --dport 1723 -j DNAT --to 10.8.1.173
-A PREROUTING -i eth0 -p 47 -j DNAT --to 10.8.1.173

-A FORWARD -i eth0 -o eth1 -p tcp --dport 1723 -j ACCEPT
-A FORWARD -i eth0 -o eth1 -p 47 -j ACCEPT

-A FORWARD -i eth1 -o eth0 -p 47 -j ACCEPT
-A FORWARD -i eth1 -o eth0 -p tcp --dport 1723 -j ACCEPT
-A FORWARD -i eth0 -o eth1 -m state --state ESTABLISHED,RELATED -j ACCEPT 
-A POSTROUTING -o eth0 -j SNAT --to 192.168.1.73


The vpn server is configure corectly I test with a router with port forwading.
Please tell me what is wrong and how i shoud configure to work.

Thanks and sorry for my english
Dragos

---

