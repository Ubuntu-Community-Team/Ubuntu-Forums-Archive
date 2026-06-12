---
title: "Local Network over a router"
date: 2009-08-07
forum: Networking &amp; Wireless
---

### Post by borncrusader on 2009-08-07
I have a router with 4 ethernet ports and also having wireless capability. How can I establish a local network between my PC (connected to one of the ethernet connectors) and my laptop(wireless) in *Ubuntu (Hardy/Jaunty/Karmic).

---

### Post by Adina on 2009-08-07
first you need to assign static ip addresses to the machines on your local network. in /etc/network/interfaces you need to setup somthing like this depending on your ip subnet.


> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static

address 192.168.0.60
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1


now see if you can ping machine 1 from machine 2 and vice versa. if you can then you have a local network.

---

### Post by superprash2003 on 2009-08-07
if you intend to share files and folders then take a look at SAMBA

---

