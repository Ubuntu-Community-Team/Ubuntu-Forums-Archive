---
title: "Two NIC Cards: One Internal, One External"
date: 2009-10-01
forum: Networking &amp; Wireless
---

### Post by f00fster on 2009-10-01
I was looking to setup two NIC cards. So far I have the following:

root@server:~# cat /etc/network/interfaces
auto lo eth0
iface lo inet loopback

iface eth0 inet static
        address 192.168.168.13
        netmask 255.255.255.0
        gateway 192.168.168.1



iface eth1 inet static
        address 69.61.132.150
        netmask 255.255.255.248
        broadcast 69.61.132.148
        network 69.61.132.144

root@server:~# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.8.0.0        0.0.0.0         255.255.255.0   U     0      0        0 as0t0
192.168.168.0   0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.168.1   0.0.0.0         UG    100    0        0 eth0

What am I doing wrong?

Hwo do i get the external static ip on one interface while having the internal one on the other. I know this is basic. But this is a basic forum. And I've done my due diligence in looking for the answer.

---

