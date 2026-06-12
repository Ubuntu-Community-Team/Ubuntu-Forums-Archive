---
title: "Help with RT2500 please! :)"
date: 2010-07-16
forum: Networking &amp; Wireless
---

### Post by Whisp3r on 2010-07-16
I have a Ralink 2500 USB:

lsusb:

```
Bus 002 Device 002: ID 148f:2573 Ralink Technology, Corp. RT2501USB Wireless Adapter

```

When I plug her in, I get the following under ifconfig:

```
wlan0     Link encap:Ethernet  HWaddr 00:0c:09:20:11:87  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:893 (893.0 B)  TX bytes:621 (621.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-0C-09-20-11-87-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

IFCONFIG will let me take wlan0 up and down, but I cannot change the MAC address or put it into monitor mode. I downloaded the RT2500 driver via Synaptic, but nothing changed. What do I need to do to make this a happy wireless device? :(

---

