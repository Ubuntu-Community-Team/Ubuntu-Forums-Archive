---
title: "Dual NICs, same subnet"
date: 2013-03-28
forum: Networking &amp; Wireless
---

### Post by AnalBeard on 2013-03-28
Ok, so I have two nics, one of which i'd like to handle internet-facing traffic (eth0), and the other (gigabit nic) to handle any internal traffic; file transfers etc. now, both of the are connected to the same switch and have static ips configured. currently, when i try to bring the second nic up then i have no access to the internet etc. how should i configure the networking?

```
root@sepulveda:/home/simon# less /etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.40
netmask 255.255.255.0
gateway 192.168.1.1
broadcast 192.168.1.255
dns-nameservers 8.8.8.8

#Broadcom gigabit card
auto eth1
iface eth1 inet static
address 192.168.1.45
netmask 255.255.255.0
broadcast 192.168.1.255
dns-nameservers 8.8.8.8

```


edit: i will be using shorewall to ensure traffic traverses the right port, once i have the networking set up properly

further edit: i wrote this late at night and missed some stuff out. The machine in question isn't a gateway at all, just a storage server sitting on the network with a 100Mb and a gigabit nic.

---

### Post by Iowan on 2013-03-30
Seems that having two NICs in the same subnet (in the same machine) violates the Spanning Tree Protocol. It plays havoc with routing (to which NIC should the router send incoming traffic?).

---

### Post by AnalBeard on 2013-03-31
> **Iowan said:**
> Seems that having two NICs in the same subnet (in the same machine) violates the Spanning Tree Protocol. It plays havoc with routing (to which NIC should the router send incoming traffic?).

no very true, I did some more reading up and proxy arping will get confused with the routes flapping between the two nics. I guess the only way to achieve it is to run two different VLANs with one single nic in one of them.

---

