---
title: "internet connection problem"
date: 2010-06-08
forum: Networking &amp; Wireless
---

### Post by maclp on 2010-06-08
hallo forum,

i have a problem with my internet connection in ubuntu 8.04 server edition.

if i ping to: [www.google.com]("http://www.google.com") i get:
Destination Host Unreachable

but when i ping to my gateway or other pc's in my network no problems occur.

please help

---

### Post by dineshs on 2010-06-08
what happens when you
```
ping 4.2.2.1 -c5
```

---

### Post by maclp on 2010-06-08
> **dineshs said:**
> what happens when you
```
ping 4.2.2.1 -c5
```

i get this:
From 26.10.0.170 icmp_seq=1 Destination Host Unreachable

---

### Post by dineshs on 2010-06-08
what about
```
route -n
```

---

### Post by maclp on 2010-06-08
> **dineshs said:**
> what about
```
route -n
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
26.10.0.0       0.0.0.0         255.255.255.0       U        0     0        0   eth0
26.10.0.0       0.0.0.0         255.255.0.0           U       0      0        0   eth1
0.0.0.0         26.10.0.254     0.0.0.0               UG    100    0        0    eth1
0.0.0.0         26.10.0.254     0.0.0.0               UG    100    0        0    eth0

---

### Post by dineshs on 2010-06-08
The result shows same gateway for both the devices.Let us wait for experts to comment on this.I think this is the issue.I am not sure

---

### Post by marcio123 on 2010-06-08
Show what do You have in:

pico /etc/network/interfaces

---

### Post by maclp on 2010-06-08
> **marcio123 said:**
> Show what do You have in:

pico /etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet static
address 26.10.0.170
netmask 255.255.0.0
hwaddress ether 00:07:e9:ba:4e:97
network 26.10.0.0
gateway 26.10.0.254

---

### Post by maclp on 2010-06-08
thanks for all your help!

after some screwing around in the /etc/network/interfaces file i fixed it.

just don't ask me how, i still really have no idea what the problem was.

---

### Post by marcio123 on 2010-06-08
Nice. Paste here current content of /etc/network/interfaces.

---

### Post by maclp on 2010-06-08
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 26.10.0.160
netmask 255.255.255.0
network 26.10.0.0
gateway 26.10.0.254

---

