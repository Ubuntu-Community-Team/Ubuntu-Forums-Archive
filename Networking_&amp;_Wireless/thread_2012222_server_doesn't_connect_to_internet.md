---
title: "server doesn't connect to internet"
date: 2012-06-28
forum: Networking &amp; Wireless
---

### Post by walter_j on 2012-06-28
I upgraded a server to a hp ML150G6 proliant running ubuntu 12.04. The static ip is as follows:

auto eth0
iface eth0 inet static
netmask 255.255.255.0
# fisheries
address 192.168.1.99
network 192.168.1.0
gateway 192.168.1.1
broadcast 192.168.1.255


linksys 54g router running tomato on 192.168.1.1

The internal network works ok, but the server won't connect to the internet. All other pc's connect to the internet fine (but using dhcp). If I change to dhcp the server also connects to the internet. I use the same static settings on another server w/o problems, but this one has me stumped. Whats wrong?

---

### Post by chili555 on 2012-06-28
Please amend your file as follows:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.99
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 8.8.8.8 192.168.1.1
```Then restart the interface:```
sudo ifdown eth0 && sudo ifup eth0
```And then test:```
ping -c3 www.google.com
```

---

### Post by walter_j on 2012-07-03
worked great. thanks

---

