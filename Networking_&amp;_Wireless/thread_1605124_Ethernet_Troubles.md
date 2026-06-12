---
title: "Ethernet Troubles"
date: 2010-10-24
forum: Networking &amp; Wireless
---

### Post by SilverstepP on 2010-10-24
I revived a blackscreened windows xp computer to have Ubuntu 10.10. However, it fails to connect to the internet through a wired connection, and it has no wifi capabilities. The same exact cpu was able to get internet previously when it was working (it was an XP), and the wire is working...
 
I wish I could explain this a bit more, but I honestly have no clue why it won't connect. Auto eth0 is in the connections list, but it never shows that it's connected. Where could the problem lie?

---

### Post by amauk on 2010-10-24
Can you post the output of
```
sudo lshw -C network
```
and
```
ifconfig
```

---

### Post by SilverstepP on 2010-10-25
> **amauk said:**
> Can you post the output of
```
sudo lshw -C network
``` 
 
```

[sudo] password for silverstepp: 
*-network 
description: Ethernet interface
product: 82801BA/BAM/CA/CAM Ethernet Controller
vendor: Intel Corporation
physical id: 8
bus info: pci@0000:02:08.0
logical name: eth0
version: 03
serial: 00:03:47:c1:5f:e8
size: 10MB/s
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=32 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
resources: irq:20 memory:feaff000-feafffff ioport:df00(size=64)

```
 
> and
```
ifconfig
```
 
```

silverstepp@silverstepp-E-3600:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:03:47:c1:5f:e8 
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:136 errors:0 dropped:0 overruns:0 frame:0
TX packets:136 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:10656 (10.6 KB) TX bytes:10656 (10.6 KB)
```
 
So, what does this mean? Is something messed up?

---

### Post by Iowan on 2010-10-25
> **SilverstepP said:**
> 
So, what does this mean? Is something messed up?If *something* isn't messed up, you'd have no problem ;)
(That's supposed to be humor...)

The interface has no IP address. You might try:
```
sudo ifconfig eth0
```
You'll *probably* get a "...no DHCP offers... sleeping" message.

---

### Post by SilverstepP on 2010-10-25
> **Iowan said:**
> If *something* isn't messed up, you'd have no problem ;)
(That's supposed to be humor...) 
 
Lol, this is indeed true.
 
> **Iowan said:**
> The interface has no IP address. You might try:
```
sudo ifconfig eth0
```
You'll *probably* get a "...no DHCP offers... sleeping" message.
 
```

eth0 Link encap:Ethernet HWaddr 00:03:47:c1:5f:e8 
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

```
 
Well, that's what I got.

---

### Post by amauk on 2010-10-25
can you post the contents of /etc/network/interfaces
```
cat /etc/network/interfaces
```

---

### Post by SilverstepP on 2010-10-25
> **amauk said:**
> can you post the contents of /etc/network/interfaces
```
cat /etc/network/interfaces
```
 
Sure thing.
 
```

auto lo
iface lo inet loopback

```

---

### Post by Iowan on 2010-10-25
> **Iowan said:**
> You might try:
```
sudo ifconfig eth0
```

AWWW... #-o
Brain and fingers on different channels... 
That shoulda been:```
sudo dhclient eth0
```

---

### Post by SilverstepP on 2010-10-25
> **Iowan said:**
> You'll *probably* get a "...no DHCP offers... sleeping" message.
 
Yep, got that. So what should I do?

---

### Post by Iowan on 2010-10-25
Unfortunately, this is where my information gets sparse. I haven't seen a thread with a cure-all for this problem. Some routers seem to be problematic... but that doesn't really explain why they're biased against Ubuntu clients. 

Setting up a static address outside the DHCP range is an option - IF you know the DHCP range. Do you have access to the router setup to determine that?

---

### Post by SilverstepP on 2010-10-25
> **Iowan said:**
> Unfortunately, this is where my information gets sparse. I haven't seen a thread with a cure-all for this problem. Some routers seem to be problematic... but that doesn't really explain why their biased abainst Ubuntu clients. 
 
Setting up a static address outside the DHCP range is an option - IF you know the DHCP range. Do you have access to the router setup to determine that?
 
I don't know. I'm pretty new to this.
 
Well, I think I can see the details about it through my laptop. But, if im on the right screen, I see no 'DHCP range', only that DHCP is enabled.
 
On another note, it seems that the wifi (same connection) on my laptop works fine if i try running it in ubuntu. But the ethernet cord doesn't fit into my laptop so I can't test the ethernet...

---

