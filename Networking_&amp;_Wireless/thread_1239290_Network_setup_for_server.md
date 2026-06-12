---
title: "Network setup for server"
date: 2009-08-13
forum: Networking &amp; Wireless
---

### Post by Rmcovert on 2009-08-13
I am fairly new to ubuntu server and am trying to setup a server as a network, dns, email, and web server. I have installed all the appropriate packages with the default install.

My problem is I have 2 ethernet cards installed. I want one to be for the internal network, intranet, and one to be for the outside world, the internet. I have the cat5 cable for one of the ethernet cards plugged into a switch that is before the router and the other plugged into the router. I just don't know how to setup the ethernet cards so that from the outside world I can go to the server and also connect the inside world to the network.

Any help on the setup of the ethernet cards would be greatly appreciated.

Thanks in advance.

---

### Post by superprash2003 on 2009-08-13
you could setup itnernet connection sharing for this and use iptables to forward specific ports to specific machines so you get access to them , be it via ssh, remote desktop, ftp etc

---

### Post by Iowan on 2009-08-13
[ICS]("https://help.ubuntu.com/community/Internet/ConnectionSharing") help page. So, the server will act as router, proxy, etc for all clients? Will it also be DHCP server? You will want to set up a static address on the local (client) side. The router side could be either static or via DHCP... but should be in different subnet than the "local" card.
The router will need to be set up to "port-forward" from outside (as mentioned).

---

