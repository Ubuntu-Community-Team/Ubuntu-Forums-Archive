---
title: "Wired Connection Problem"
date: 2012-01-13
forum: Networking &amp; Wireless
---

### Post by Pluto011 on 2012-01-13
I have a dell latitude 2100 running ubuntu 11.1. Wireless internet works fine on it but wired connections do not. When I plug a ethernet cord in, it keeps on saying wired connection connected followed by disconnected. When I check the ethernet connection in the network part of system settings, it also keeps rapidly changing to on/off. I really need an ethernet connection so I can share my wifi with my desktop.

---

### Post by jsra on 2012-01-13
Hi,
can you post
```
ifconfig
cat /etc/network/interfaces
```
Are you just trying to connect two computers directly without router or switch?

---

### Post by Pluto011 on 2012-01-13
I am trying to use the shared to other computers ipv4 setting for my ethernet port.

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr b8:ac:6f:69:c2:b6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:112 errors:0 dropped:0 overruns:0 frame:0
          TX packets:112 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9752 (9.7 KB)  TX bytes:9752 (9.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:24:d6:7c:83:88  
          inet addr:192.168.1.129  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:d6ff:fe7c:8388/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21030 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19239 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18703292 (18.7 MB)  TX bytes:4875287 (4.8 MB)

```cat:
```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```

---

### Post by Pluto011 on 2012-01-15
bump

---

### Post by Pluto011 on 2012-01-15
bumpdy bump bump

---

### Post by Iowan on 2012-01-15
One bump/day (24 hours) is probably enough.
Have you tried disabling the wireless - to see if it lets the wired be more stable?

---

### Post by Pluto011 on 2012-01-24
I need both working at once.

---

