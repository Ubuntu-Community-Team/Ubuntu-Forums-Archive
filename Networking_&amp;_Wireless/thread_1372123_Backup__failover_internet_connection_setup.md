---
title: "Backup / failover internet connection setup"
date: 2010-01-04
forum: Networking &amp; Wireless
---

### Post by amitbiswas on 2010-01-04
Hello,
I want to implement backup / fail over internet connection to my ubuntu server. My interface file as below. I like to configure when eth0 interface goes down, internet gateway switch to eth1 interface. Any help in this issue will be much appreciated.

================================
auto eth0
iface eth0 inet static
address XXX.XXX.XXX.XXX
gateway XXX.XXX.XXX.XXX
netmask XXX.XXX.XXX.XXX
network XXX.XXX.XXX.XXX
broadcast XXX.XXX.XXX.XXX

auto eth1
iface eth1 inet static
address XXX.XXX.XXX.XXX
gateway XXX.XXX.XXX.XXX
netmask XXX.XXX.XXX.XXX
network XXX.XXX.XXX.XXX
broadcast XXX.XXX.XXX.XXX

Thank you - Amit

---

