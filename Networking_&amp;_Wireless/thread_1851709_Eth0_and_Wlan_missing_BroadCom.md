---
title: "Eth0 and Wlan missing? BroadCom"
date: 2011-09-28
forum: Networking &amp; Wireless
---

### Post by bhaarat316 on 2011-09-28
Hey guys, I'm pretty new to ubuntu having problems with my wiirless card.  Broadcom b/g/n card for dell E1405, Broadcom Corporation BCM4321 802.11a/b/g/n [14e4:4328

Now I finally got the wifi to work, but I want to set up a bridge and use my laptop as a wired connection.  Now when I go to the wired connects and change to share this computer and plug in the wire nothing happens.  The lights are on, where the wire is plugged in as orange and red .  

When i do ifconfig it gives me something like eth2 and crazy words instead of ip address and the usual.  Wlan shows up as lo.

Any ideas how I can fix this? I"m even willing to just scrap the driver and reinstall.

I just want to bridge my laptop and xbox. I've done it before with 10. But when I changed too 11.04 while installing the drivers something went wrong.

---

### Post by bhaarat316 on 2011-09-28
eth2      Link encap:Ethernet  HWaddr 00:16:cf:0e:ea:9c  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:cfff:fe0e:ea9c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:71078 errors:1 dropped:0 overruns:0 frame:56526
          TX packets:52402 errors:28 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:87899128 (87.8 MB)  TX bytes:9289177 (9.2 MB)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:817 errors:0 dropped:0 overruns:0 frame:0
          TX packets:817 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:67800 (67.8 KB)  TX bytes:67800 (67.8 KB)

---

