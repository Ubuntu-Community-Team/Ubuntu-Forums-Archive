---
title: "[SOLVED] Network stops working internittently"
date: 2009-01-11
forum: Networking &amp; Wireless
---

### Post by aheckler on 2009-01-11
Not very often, but on occasion, my network connection will just seem to stop working. I'll be browsing the Internet and suddenly nothing will load, for example.

When this happens, I usually try 
```
sudo ifdown eth0 && sudo ifup eth0
```
to reset the connection, but sometimes this will say my hostname could not be resolved.

What's more, "ifconfig" retuns 2 extra networks, pan0 and pan0:avahi. These seem to have something to do with Bluetooth, but they weren't there just a few days ago.
```
eth0      Link encap:Ethernet  HWaddr 00:15:58:96:f6:e0  
          inet addr:134.53.101.216  Bcast:134.53.101.255  Mask:255.255.255.0
          inet6 addr: fe80::215:58ff:fe96:f6e0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1745 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1780 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1084591 (1.0 MB)  TX bytes:249307 (249.3 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:62 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4712 (4.7 KB)  TX bytes:4712 (4.7 KB)

pan0      Link encap:Ethernet  HWaddr 42:be:b3:be:6c:1c  
          inet6 addr: fe80::40be:b3ff:febe:6c1c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:5095 (5.0 KB)

pan0:avahi Link encap:Ethernet  HWaddr 42:be:b3:be:6c:1c  
          inet addr:169.254.6.155  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
```

For reference, my resolv.conf is:
```
domain muohio.edu
search muohio.edu
nameserver 208.67.222.222
nameserver 208.67.220.220
nameserver 134.53.13.17
nameserver 134.53.13.1
```

Halp!

EDIT: I fixed the pan0 and pan0:avahi networks by removing all the Bluetooth packages.

---

### Post by aheckler on 2009-01-11
Solved it by changing /etc/hosts as described in [this thread]("http://ubuntuforums.org/showthread.php?t=723361").

---

