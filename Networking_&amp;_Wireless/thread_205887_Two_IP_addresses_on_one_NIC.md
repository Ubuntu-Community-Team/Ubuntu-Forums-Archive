---
title: "Two IP addresses on one NIC"
date: 2006-06-29
forum: Networking &amp; Wireless
---

### Post by lzap on 2006-06-29
Hello,

how can I *properly* configure **two IP addresses on one ethernet card**? I mean - not by modifing rc.local, but with some modification of Ubuntu`s network startup scripts configuration...

Thank you

---

### Post by Mekik on 2006-06-29
try this out..
ifconfig dummy machine_name
route add machine_name

---

### Post by lzap on 2006-06-29
$ cat interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 10.132.76.80
netmask 255.255.255.0
gateway 10.132.76.1

auto eth0:1
iface eth0:1 inet static
address 213.192.23.227
netmask 255.255.255.0
gateway 213.192.23.17

---

