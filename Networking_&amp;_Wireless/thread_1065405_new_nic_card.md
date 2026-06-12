---
title: "new nic card"
date: 2009-02-09
forum: Networking &amp; Wireless
---

### Post by kinalas on 2009-02-09
here is my present setup (interfaces)

auto lo
iface lo inet loopback
auto eth1

iface eth1 inet static
address 192.168.0.150
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1
dns-nameservers 192.168.0.1

nic is connected to the router (192.168.0.1)

i added a new nic coz i'm planning to make this ubuntu server a proxy server

what will be the additional settings on my interfaces if i will have an ip address 192.168.0.151

---

