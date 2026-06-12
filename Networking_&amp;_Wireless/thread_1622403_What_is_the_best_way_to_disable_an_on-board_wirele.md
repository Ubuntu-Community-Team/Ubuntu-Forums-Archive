---
title: "What is the best way to disable an on-board wireless device?"
date: 2010-11-15
forum: Networking &amp; Wireless
---

### Post by Beamvr6 on 2010-11-15
Hi,

I recently bought a new nettop and installed Ubuntu 10.10 Desktop. Unfortunately the on-board wlan is kind of crap so I bought a USB Wireless stick and since that stick has a pretty recent chipset ndis was needed to get the USB stick to work as wlan1.

The issue is I want to disable the on-board wlan (wlan0). The BIOS does not offer that option so it needs to be done in the OS I guess. My question is what is the best way of doing so? I've read something about blacklisting or editing 10-wlan.rules but I am unsure what the best place is and what to put there.

This the output of ifconfig:

> eth0      Link encap:Ethernet  HWaddr 00:01:2e:2b:a7:b0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:30 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2197 (2.1 KB)  TX bytes:2197 (2.1 KB)

wlan0     Link encap:Ethernet  HWaddr 74:f0:6d:2b:0b:a7  
          inet addr:192.168.1.76  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::76f0:6dff:fe2b:ba7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26908 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13277 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7233635 (7.2 MB)  TX bytes:1672211 (1.6 MB)

wlan1     Link encap:Ethernet  HWaddr 00:0c:f6:93:7c:70  
          inet addr:192.168.1.75  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:f6ff:fe93:7c70/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:68746 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53522 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:42686547 (42.6 MB)  TX bytes:7375475 (7.3 MB)


The driver for wlan0 is ath9k.

TIA.

---

### Post by chili555 on 2010-11-15
Please try this:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add a new line:```
blacklist ath9k
```Proofread carefully, save and close gedit. Now do:```
sudo rmmod -f ath9k
```How is it working now?

---

### Post by Beamvr6 on 2010-11-15
Works like a charm! Thanks a lot. :)

---

