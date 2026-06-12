---
title: "Two NICs on same network"
date: 2010-05-05
forum: Networking &amp; Wireless
---

### Post by discCellIT on 2010-05-05
We have a Ubuntu machine running running an nginx webserver which has three NICs. Two NICs are on the same network and we want it to respond to each IP address statically.  The problem is that when a request comes in on eth2 the reply always goes out on eth1. 
 How do i configure it so that what comes in an interface also goes back out the same one? 
This is the current configuration in /etc/network/interfaces 

auto eth0 
iface eth0 inet static 
address 67.137.23.72 
    netmask 255.255.255.224 
    network 67.137.23.64 
    broadcast 67.137.23.95 
    gateway 67.137.23.65  

iface eth2 inet static 
address 67.137.23.76 
    netmask 255.255.255.224 
    network 67.137.23.64 
    broadcast 67.137.23.95 
auto eth2  

iface eth1 inet static 
address 20.2.2.28 
netmask 255.255.255.0  
auto eth1 
----------- 
 Any help or direction would be greatly appreciated.

---

