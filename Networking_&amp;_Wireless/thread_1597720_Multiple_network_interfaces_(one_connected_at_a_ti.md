---
title: "Multiple network interfaces (one connected at a time)"
date: 2010-10-15
forum: Networking &amp; Wireless
---

### Post by wwwerewolf on 2010-10-15
Hello, could anyone help me configure a server with two network interfaces?  This system is physically moved from one network to another every few days (different buildings but connected by a VPN).

I'd like to be able to control the IP address of the system depending on which port I plug the network cable into with a static setting.

Right now the system will connect to the local network, but any requests to go beyond the subnet get lost.

The only way I can get the system to talk outside of its subnet is to comment out the second interface.


/etc/network/interfaces:
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.67.95
gateway 192.168.67.2  #Yes, this should be 2, not 1
netmask 255.255.255.0
network 192.168.67.0
broadcast 192.168.67.255

auto eth1
iface eth1 inet static
address 192.168.1.95
gateway 192.168.1.1 #Yes, this should be 1, not 2
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255


Thanks for any help.

---

### Post by pricetech on 2010-10-15
Do you have access to the DHCP servers at the locations where this server will be used ??  If so, set the routers to reserve an IP for the mac of your eth0 (or eth1, doesn't matter which) and use just that NIC.

But if you continue to use fixed IPs you'll have to at least do away with the gateway for the unused interface.

---

### Post by wwwerewolf on 2010-10-18
pricetech,
   Thanks for the suggestion.
   I was hoping to hard code everything on the system so as not to rely on any outside systems (so to speak), but I may just have to try that.

---

