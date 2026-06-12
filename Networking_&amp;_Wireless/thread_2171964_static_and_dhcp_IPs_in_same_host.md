---
title: "static and dhcp IPs in same host"
date: 2013-09-02
forum: Networking &amp; Wireless
---

### Post by Suresh_Rajachar on 2013-09-02
Hi, 

I am trying to use netsed to modify TCP packets in-fly. Below is the interfaces files of two ubnutu PCs:

_PC1_
auto lo
iface lo inet loopback

auto eth0
allow-hotplug eth0
iface eth0 inet dhcp
   pre-up   ifconfig $IFACE up
   pre-down ifconfig $IFACE down

auto eth1
allow-hotplug eth1
iface eth1 inet static
address <Static IP address1>
network <gateway IP address>
netmask 255.255.0.0
gateway <gateway IP address>
pre-up   ifconfig $IFACE up
pre-down ifconfig $IFACE down



_PC2_
auto lo
iface lo inet loopback

auto eth0
allow-hotplug eth0
iface eth1 inet static
address <Static IP address2>
network <Static IP of eth1 of PC1>
netmask 255.255.0.0
gateway <Static IP of eth1 of PC1>
pre-up   ifconfig $IFACE up
pre-down ifconfig $IFACE down

#auto eth1
#allow-hotplug eth1
#iface eth1 inet dhcp


Both PC and PC2 have been physically connected with crossover cable. 

But bot the PCs are not able to access internet. When i renove the static IP of eth1 of PC1 then only PC1 can access the internet.

Can anyone please suggest what else need to be configured so that PC1 acts as gateway for PC2 ? 

I am using Ubuntu 12.04.3 LTS in both the PCs

Thanks in adancve. 
-Suresh

---

