---
title: "Tunnel Traffic"
date: 2009-07-01
forum: Networking &amp; Wireless
---

### Post by acidone on 2009-07-01
I have a Ubuntu Box sitting out on the internet and I want to tunnel all my traffic, all ports, coming in to a computer on my local network computer (Win2k8) and the same going the opposite direction.

Here's the setup:
External Computer:
ETH0: 10.10.10.79 (External)
255.255.255.224
ETH1: 192.168.33.6
255.255.255.0

Internal Computer:
NIC: 192.168.33.86
255.255.255.0

What would be the best way to accomplish this? SSH, VPN, IPTable Port forwarding? The internal computer runs some web and mail services that I want to be able to access from the External's IP. There is no router or anything infront of my ubuntu box it's wide open.

Thanks in advance.
-B

---

### Post by jonobr on 2009-07-01
Hello


Maybe you could take a look at opevpn daemon on the server and setup an open VPN client on your other side.
I have not done this myself.
Openvpn is available if you go to synaptic, and configuring it can be done using the gui client and gui server.

The openvpn website has a documentation [HERE]("http://openvpn.net/index.php/open-source/documentation.html")

---

### Post by Brandon Williams on 2009-07-01
It sounds like you want your Ubuntu box to be an internet gateway/router for your internal network (or, at least for one of the machines on your internal network). The most straightforward way to do this would be to configure port-forwarding, NAT, and filtering rules with iptables. You can find documentation about how to do everything you need to do [here](http://www.netfilter.org/).

---

### Post by hackertarget on 2009-07-03
Definitely check out OpenVPN. It will give you full access from your remote client to your internal LAN (ie the internal host as well as any others). Everything will also be encrypted over the connection keeping your interal LAN more secure. You will only need to have a single port open on your external host.

I have just been setting it up myself and have just (5mins ago) completed a guide to setting up on Jaunty.

[http://hackertarget.com/2009/07/guide-to-openvpn-on-ubuntu-904-jaunty-jackalope/](http://hackertarget.com/2009/07/guide-to-openvpn-on-ubuntu-904-jaunty-jackalope/)

I have not tested this setup with a windows client but cannot see any major problems by using one.

---

### Post by superprash2003 on 2009-07-03
are oyu trying to share an internet connection?

---

