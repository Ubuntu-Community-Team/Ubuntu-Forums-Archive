---
title: "Download Speeds Degrade over time"
date: 2011-06-01
forum: Networking &amp; Wireless
---

### Post by ryan00793 on 2011-06-01
Well, within 30-60 ish seconds my download speed hits 100bs - 1kbs and I have no rhyme or reason for why its doing this. I do not really modify anything in linux because i hardly use ubuntu for this reason. So i have no information other then it slows down however if you ask me to get you specific information i will try to be looking at this page a lot.
Any way on to what i have,

Ubuntu: 10.04 (lucid) (32 Bit)
Gnome: 2.30.2 (Ubuntu 2010-06-25)
Kernel:  2.6.32-32-generic (#62-Ubuntu SMP Wed Apr 20 21:54:21 UTC 2011)
GCC :    4.4.3 (i486-linux-gnu)

PS Thanks for any help =]

*EDIT*
Also it doesn't matter what network adapter  i use, I have tried 4 different things all with the same result

---

### Post by ryan00793 on 2011-06-02
> **ryan00793 said:**
> Well, within 30-60 ish seconds my download speed hits 100bs - 1kbs and I have no rhyme or reason for why its doing this. I do not really modify anything in linux because i hardly use ubuntu for this reason. So i have no information other then it slows down however if you ask me to get you specific information i will try to be looking at this page a lot.
Any way on to what i have,

Ubuntu: 10.04 (lucid) (32 Bit)
Gnome: 2.30.2 (Ubuntu 2010-06-25)
Kernel:  2.6.32-32-generic (#62-Ubuntu SMP Wed Apr 20 21:54:21 UTC 2011)
GCC :    4.4.3 (i486-linux-gnu)

PS Thanks for any help =]

*EDIT*
Also it doesn't matter what network adapter  i use, I have tried 4 different things all with the same result

*EDIT 2*
Just disabled IPV6 to see if that would help

---

### Post by garvinrick4 on 2011-06-02
What is your network card?
Run this in terminal and post so we can see card and driver:
```
sudo lshw -C network
```

---

### Post by ryan00793 on 2011-06-02
> **garvinrick4 said:**
> What is your network card?
Run this in terminal and post so we can see card and driver:
```
sudo lshw -C network
```


```
  *-network:0             
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: wlan0
       version: 00
       serial: 00:1e:e5:9f:63:d0
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci ip=192.168.2.36 latency=32 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:e6000000-e6007fff
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 78
       serial: 00:0e:a6:c6:d3:81
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=192.168.2.37 latency=32 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100MB/s
       resources: irq:23 ioport:cc00(size=256) memory:e600a000-e600a0ff

```

---

### Post by garvinrick4 on 2011-06-05
Sorry I missed your post I thought you were done when no reply.
I will bump this up to the front and see if any user has skills in
that card and driver.
rt61pci is the driver and I looked around and just found bug reports and no fix's.
Need someone who has dealt with that driver.

The edit you have about using multiple adapters and not getting a steady connection.
Have you looked at your router settings? 4 different adapters and none working is just
not usual at all. Most drivers are in the linux kernel and work. A few restricted here and
there that need installing from repositories but this is looking more like router if all do
the same thing.

---

### Post by ryan00793 on 2011-06-06
> **garvinrick4 said:**
> Sorry I missed your post I thought you were done when no reply.
I will bump this up to the front and see if any user has skills in
that card and driver.
rt61pci is the driver and I looked around and just found bug reports and no fix's.
Need someone who has dealt with that driver.

The edit you have about using multiple adapters and not getting a steady connection.
Have you looked at your router settings? 4 different adapters and none working is just
not usual at all. Most drivers are in the linux kernel and work. A few restricted here and
there that need installing from repositories but this is looking more like router if all do
the same thing.

Well I tend to not think its a router problem since i have 5 other computers working fine (2 wired [servers] and 3 laptops then this desktop) and im also inclined to think its linux since my XP partition works just fine... Thanks for trying to help though :popcorn:

EDIT and the connection works fine after rebooting

---

