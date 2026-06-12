---
title: "Broadcom STA Injection Patch"
date: 2010-08-25
forum: Networking &amp; Wireless
---

### Post by HeroKing on 2010-08-25
i'm having trouble trying to install the correct injection patch i need for my wireless driver. i looked in the directory lib/modules/2.6.32-24-generic/kernel/drivers/net/wireless/ and found i have folders for both b43 and b43legacy. though it was my understanding i needed a bcm43xx patch from all the threads/tutorials i looked through.

my current set up is as follows

ifconfig:
```
eth1      Link encap:Ethernet  HWaddr 00:1f:e1:26:5f:87  
          inet addr:10.202.208.124  Bcast:10.202.208.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:e1ff:fe26:5f87/64 Scope:Link
          UP BROADCAST RUNNING  MTU:1500  Metric:1
          RX packets:165205 errors:0 dropped:0 overruns:0 frame:145547
          TX packets:147150 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:178295183 (178.2 MB)  TX bytes:28597339 (28.5 MB)
          Interrupt:19
```

lspci -nn
```
05:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
06:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
```

and when i try to run airodump, i get this:

```
ioctl(SIOCSIWMODE) failed: Invalid argument

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead.  Make
sure RFMON is enabled: run 'airmon-ng start eth1 <#>'
Sysfs injection support was not found either.
```

i could tell from this i needed the injection patch, but i can't find one anywhere that matches my kernel - 2.6.32-24-generic. if anyone has the patch that can work w/my setup, please help

---

