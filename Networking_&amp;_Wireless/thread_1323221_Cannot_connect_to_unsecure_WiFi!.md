---
title: "Cannot connect to *unsecure* WiFi!"
date: 2009-11-11
forum: Networking &amp; Wireless
---

### Post by lvlammert on 2009-11-11
New HP Mini 110, fresh UNR 09.10, updated, Broadcom

Installed 09.10 & then Broadcom drivers,.. connected just fine to local WIFi w/WEP. Imagine my surprise when I tried to connect to an unsecure public hotspot AND THE APPLET ICON JUST SPUN AWAY AND TIMED OUT!

All networks appear correctly in the list, .. connected to two different *secure* networks with no problem, but cannot connect to an *unsecure* network. Almost seems like there's a switch somewhere preventing an unsecure connection!

Cannot find any other posts OT, .. dmesg:

[    9.409936] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.91.9

ifconfig:

eth2      Link encap:Ethernet  HWaddr 0c:60:76:2a:15:10  
          inet6 addr: fe80::e60:76ff:fe2a:1510/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:134786 errors:210 dropped:0 overruns:0 frame:46987
          TX packets:102792 errors:117 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:140883449 (140.8 MB)  TX bytes:25741686 (25.7 MB)
          Interrupt:16 Base address:0xc000 

iwconfig:

eth2      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   

I had an identical Mini in June with 09.04 and had no trouble at all, .. so either the h/w is different or there might be an issue with 09.10??

    TIA,

    Lee

---

### Post by lvlammert on 2009-12-02
More info:

After working fine with secure APs on the road recently, .. I'm back in town and back to the original problem - my AP at the shop is WEP, but I CANNOT connect to an open AP (e.g. Panera) WITHOUT REBOOTING THE MACHINE!

Is there any way to 'reset' the Broadcom driver to avoid a reboot:

    Lee

PS - Got one reply asking for more info, but it was not posted here on the forum.

---

