---
title: "hyper-v networking"
date: 2012-04-18
forum: Networking &amp; Wireless
---

### Post by ant0n10 on 2012-04-18
I installed 12.1 beta on a W2K8 R2 box using hyper-v, I have another virtual OSs running there and they are able to access internet but Ubuntu cannot get connected, as this my first Linux installation I guess there is a trick to work around it.

In my virtual W2K3, I have the following configuration:
192.168.1.112 [IP Addres]
255.255.255.0 [Subnet mask]
192.168.1.1   [Default gateway]
192.168.1.69  [DNS]

so I found the following documentation, 
[http://www.isummation.com/blog/installing-ubuntu-server-1104-64bit-on-hyper-v/](http://www.isummation.com/blog/installing-ubuntu-server-1104-64bit-on-hyper-v/)

and tried the following but not luck,

$sudo vi /etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.20
netmask 255.255.255.0
gateway 192.168.1.1


Any clues. 

Thanks,
ant0n10

---

