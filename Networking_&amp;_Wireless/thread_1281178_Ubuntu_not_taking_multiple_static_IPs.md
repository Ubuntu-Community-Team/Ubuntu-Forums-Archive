---
title: "Ubuntu not taking multiple static IPs"
date: 2009-10-03
forum: Networking &amp; Wireless
---

### Post by sreeraj on 2009-10-03
I am using Ubuntu 9.04. I have assigned multiple static IPs to the same NIC. But the problem is that ubuntu is taking onlt the first address. My configuration in /etc/network/interfaces is as follows. Please help

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet static
        address 192.168.0.34
        netmask 255.255.255.0
        broadcast 192.168.0.255

auto eth1:0
iface eth1:0 inet static
        address 192.168.0.1
        netmask 255.255.255.0
        broadcast 192.168.0.255

auto eth2
iface eth2 inet dhcp

---

### Post by Iowan on 2009-10-04
Try using eth1:1 instead of eth1:0... in case eth1 and eth1:0 are interpreted as the same.

---

### Post by gradinaruvasile on 2009-10-04
What does 'ifconfig' return? And 'ip rou' ?

---

