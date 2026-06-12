---
title: "flushing routing tables"
date: 2011-11-21
forum: Networking &amp; Wireless
---

### Post by stanjest on 2011-11-21
Hello
I executed route -FC and the result is shown below
steven@steven-desktop:~$ route -FC
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     1      0        0 eth0
169.254.0.0     *               255.255.0.0     U     1000   0        0 eth0
Kernel IP routing cache
Source          Destination     Gateway         Flags Metric Ref    Use Iface
192.168.1.1     all-systems.mca all-systems.mca ml    0      0        0 lo
steven-desktop. 224.0.0.251     224.0.0.251     ml    0      0        0 eth0
steven-desktop. 192.168.1.255   192.168.1.255   bl    0      0        4 eth0
192.168.1.100   192.168.1.255   192.168.1.255   ibl   0      0        2 lo
192.168.1.100   255.255.255.255 255.255.255.255 ibl   0      0      144 lo
steven-desktop. 192.168.1.255   192.168.1.255   bl    0      0        5 eth0
192.168.1.100   192.168.1.255   192.168.1.255   ibl   0      0        2 lo
*               255.255.255.255 255.255.255.255 bl    0      0        0 lo
192.168.1.100   255.255.255.255 255.255.255.255 ibl   0      0      170 lo
192.168.1.1     steven-desktop. steven-desktop. il    0      0        7 lo
Green.local     224.0.0.251     224.0.0.251     ml    0      0        6 lo
The question is how can I flush the ip address 192.168.1.255 from this table? Where does this table resides, such that I can permantly remove it.

---

