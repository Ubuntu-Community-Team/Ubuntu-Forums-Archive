---
title: "Ubuntu 8.04 box plugged into wireless router cannont access internet"
date: 2010-06-05
forum: Networking &amp; Wireless
---

### Post by j_70 on 2010-06-05
I have I fileserver on my home network. It has a static IP and is plugged into the back of the wireless router. It is fine on the network but cannot access the internet. I noticed this when I was trying to update my package list. This is what is in /network/ interfaces:

auto eth0
iface eth0 inet static
address 192.168.2.100
netmask 255.255.255.0
network 192.168.2.1
broadcast 192.168.2.255
gateway 192.168.2.1

auto lo
iface lo inet loopback


This is the output of route -n:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.2.1     0.0.0.0         UG    100    0        0 eth0


I am sure I have something configured wrong, I am just not sure what. TIA.

---

### Post by Iowan on 2010-06-05
Can you ping internet by IP address (74.125.95.104)?  If that works, check contents of */etc/resolv.conf*.

---

### Post by j_70 on 2010-06-06
I was able to resolve this, but, am not sure how. The network/interfaces entry represents some changes I had made. Restarting network services did not seem to work. After I rebooted the box, I could access the internet.

---

