---
title: "Wireless computer bridge/forward connection to wired computer?"
date: 2009-09-21
forum: Networking &amp; Wireless
---

### Post by teimu on 2009-09-21
Hi Ubuntu!

I'd like to "bridge" (perhaps incorrect term) or "forward" an internet connection from one computer to another, and *still use the internet on that middle computer.* In other words, the middle computer should act as both a regular computer and a router for the end computer.

I've got two computers: 1. My laptop, which is running ubuntu 9.04 and has wireless and wired network devices. If possible, this would be the "middle" computer. And, 2. My desktop, running XP with only a wired network device. This is the "end" computer.

My house right now only has wireless, and as stated, this is good for my laptop but not my desktop.

So, visually, here's what I'm trying to achieve:
```

Internet -> Laptop -> Desktop
          |         |
     (wireless)   (wired)
```

Is this possible to do? I've read up a bit on bridging, but it seems to me that this technique treats two devices the same. Also, I don't know if this is applicable, but **I do not have crossover cable, only standard straight through cable.**

In case you'd like to write come code (probably for /etc/network/interfaces), here is some extra information:
[LIST]
[*]ifconfig info
```
eth0      Link encap:Ethernet  HWaddr 00:13:a9:fb:a4:7a  
          inet6 addr: fe80::213:a9ff:fefb:a47a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:121 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18490 (18.4 KB)  TX bytes:2178 (2.1 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:74 errors:0 dropped:0 overruns:0 frame:0
          TX packets:74 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6822 (6.8 KB)  TX bytes:6822 (6.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:13:e8:70:09:d1  
          inet addr:10.0.0.5  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:e8ff:fe70:9d1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2494 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2251 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2206898 (2.2 MB)  TX bytes:448408 (448.4 KB)

```
[*]/etc/network/interfaces file
```
auto lo
iface lo inet loopback

```
[/LIST]

Thanks Ubuntu community! I'd really love to avoid buying a wireless network adapter if at all possible.

---

