---
title: "Ubuntu Oneiric Ocelot 11.10 VLan not work with me"
date: 2012-02-27
forum: Networking &amp; Wireless
---

### Post by ak.elsaman on 2012-02-27
1.install oneiric 11.10
2.apt-get install vlan
_3. vi _/etc/network/interfaces
**********
auto eth0
iface eth0 inet static
address 192.168.1.5
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

auto eth0.1
iface eth0.1 inet static
address 10.0.0.1
netmask 255.255.255.0
network 10.0.0.0
broadcast 10.0.0.255
**********

when ping eth0 (192.168.1.5) it reply from machine 192.168.1.2
but when ping eth0.1 (10.0.0.1) from machine 10.0.0.8 Network Host unreachable

i spen more than 48 hour in this problem please any help i will get crazy :S

---

