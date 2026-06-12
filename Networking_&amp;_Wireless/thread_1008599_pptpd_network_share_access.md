---
title: "pptpd network share access"
date: 2008-12-11
forum: Networking &amp; Wireless
---

### Post by bqm3043 on 2008-12-11
I have Ubuntu 8.10 installed, with pptpd for vpn access. A Windows XP client can connect to the Ubuntu pptpd server. It works perfectly in the server. The problem is I don't have access to any other computer on the network, through the vpn connection. Full access is available if sitting at any computer on the network. I have three machines behind a router.

192.168.2.26 Ubuntu 8.10 pptpd server
192.168.2.7 Ubuntu 8.04
192.168.2.17 Xubuntu 8.04

pptpd.conf has the following settings, which are the default settings.

localip  192.168.0.1
remoteip 192.168.0.234-238,192.168.0.245

Any help would be greatly appreciated.

---

### Post by iskandarjon on 2008-12-13
U can do ping through VPN by adding command to the prompt

[B]# echo 1 > /proc/sys/net/ipv4/ip_forward
# echo 1 > /proc/sys/net/ipv4/ip_dynaddr
# iptables -t nat -A POSTROUTING -o eth0 -s 192.168.0.0/24 -j MASQUERADE
[/B]
Here is the **192.168.0.0** address which Server gives dynnamic ip address for clients

This example look's like

**(vpn client)-------VPN---------(Your server)--------eth0--------(Other PC)**

If you will ping "Other PC"
**vpn client # ping "Other PC"** # it will run

---

### Post by bqm3043 on 2008-12-15
Thanks for the reply. I have a few questions.

1. According to [http://www.poptop.org](http://www.poptop.org) the problem can be solved by changing the client subnet. Since mine is 192.168.2.*, I changed the remoteip to 192.168.2.101-105 in pptp.conf. Still doesn't work.

2. The ppp subnet mask is 255.255.255.255, when the ech0 subnet mask is 255.255.255.0. If I could change this, would it solve the problem? If so, how is it changed.

3. I turned on Proxy ARP in the Netopia DSL Modem. It didn't help any.

4. Will your suggestion allow full access, or will it just handle a ping?

There is numerous folks with this same problem, but I've found do solution, which actually works. Thanks again for your help.

---

