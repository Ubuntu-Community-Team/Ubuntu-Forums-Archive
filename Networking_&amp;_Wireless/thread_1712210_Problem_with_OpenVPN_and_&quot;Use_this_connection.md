---
title: "Problem with OpenVPN and &quot;Use this connection for...&quot;"
date: 2011-03-22
forum: Networking &amp; Wireless
---

### Post by crazycoders on 2011-03-22
Hi,

I have a strange problem that i can't seem to fix by myself.

I use Ubuntu 10.10 and the latest openvpn + network-manager-openvpn.

If i setup a VPN connection it works only half way. I can connect but when i check the "Use this connection only for resources on it's network", i can't access my VPN resources but i can browse the web. If i uncheck the "Use this connection..." then i can't browse but i can reach the VPN destinations.

I have 4 ip adresses that i'm suposed to be able to reach when in the vpn: 

10.245.14.120 plutoniq-dev
10.245.14.121 plutoniq-web1
10.245.14.121 plutoniq-web2
10.245.14.122 plutoniq-web3

Gateway is ns1.plutoniq.com to connect to it.

My local network is 192.168.1.* and the gateway is 192.168.1.111

So i'm wondering if there is anyway to create routes to keep the "Use this connection" working so i can browse the web while connected to the VPN but also be able to reach my 4 ip adresses on the VPN connection.

Last but not least, here is a route dump:
mathieu@ordimath:~$ ip route ls
207.253.240.131 via 192.168.1.111 dev eth0  proto static 
10.245.1.37 dev tun0  proto kernel  scope link  src 10.245.1.38 
192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.184  metric 1 
10.245.0.0/23 via 10.245.1.37 dev tun0  proto static 
169.254.0.0/16 dev eth0  scope link  metric 1000 
default via 192.168.1.111 dev eth0  proto static 

Thankx

---

### Post by crazycoders on 2011-03-22
Finaly got a fix but i feel its a very dirty fix.

I created a launch script that launches openvpn with my config file stored locally and after sleeping the script for 5 seconds (Because i launch it as a daemon) i add routes to the system dynamically and force the 4 ip to go through TUN0 instead of the default gateway.

So now, i still have my web and all my stuff and if i launch my script, i activate my vpn connection as a daemon and create routes to my targets.

All ends well, although its a very dirty approach

---

