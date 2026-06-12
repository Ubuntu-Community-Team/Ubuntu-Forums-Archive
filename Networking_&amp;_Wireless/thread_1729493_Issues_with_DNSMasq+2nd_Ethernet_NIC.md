---
title: "Issues with DNSMasq+2nd Ethernet NIC"
date: 2011-04-15
forum: Networking &amp; Wireless
---

### Post by espressobeanie on 2011-04-15
I have a setup like this:

(LOCAL LAN) <--------(eth1)[box](eth0)------------> (My ISP)

I've configured Shorewall to allow me to pass traffic from eth1(LOC) to eth0(NET). The problem is that any incoming connection from 'Local LAN' isn't going to have a clue what to do because 'eth1' isn't setup to handle any incoming traffic. I'm trying to setup DNSMasq, to listen on eth1 for incoming traffic in my 'Local LAN', but I have no clue where to begin.

I type dnsmasq -i eth1, and it says, "Failed to create listening socket. Already in use" Do I have to change my /etc/network/interfaces by leaving out eth1?

---

