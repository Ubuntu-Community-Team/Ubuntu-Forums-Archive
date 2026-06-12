---
title: "No Wireless Networks Detected"
date: 2010-11-21
forum: Networking &amp; Wireless
---

### Post by gresavage on 2010-11-21
i think i have broken my internet... i've tried every fix i could find. I'm on a Dell Inspiron 1420 running Ubuntu 10.10 lucid lynx using a BCM4312 LP-PHY

i've tried everything to get my wireless networks to connect but nothing works. I finally got my computer to recognize my wireless card but it doesn't detect or connect to networks. Before i was able to at least see the networks but not connect or stay connected once i disconnected the ethernet cable. i will post the output of ifconfig, iwconfig, iwlist scan

---

### Post by gresavage on 2010-11-21
so apparently my computer isn't recognizing my wireless card again... soooo i need halp

ifconfig gives:

eth0      Link encap:Ethernet  HWaddr 00:1e:c9:08:60:54  
          inet addr:192.168.2.28  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: 2002:474f:4265:1234:21e:c9ff:fe08:6054/64 Scope:Global
          inet6 addr: fe80::21e:c9ff:fe08:6054/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1510 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1493 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:986024 (986.0 KB)  TX bytes:205614 (205.6 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:39 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1627 (1.6 KB)  TX bytes:1627 (1.6 KB)


iwconfig gives:


lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

before i used to have wlan0 and then wlan0:avahi they used to pop up when i typed in iwconfig now neither exists. and under my wired connections there exists a "ifupdown (wlan0)" and it's just a duplicate of my eth0 connection. except auto eth0 is now auto ethernet. I tried ndiswrapper. wicd. some other things and so many web pages and i've only seemed to have gone backwards. help is appreciated

---

### Post by gresavage on 2010-11-21
okay so now i'm back to the point where i can detect wireless networks and connect to them but only while my ethernet cable is still plugged into the router. IDK what to do. ( i went to System>Aministration>Additional Drivers and reactivated the B43 driver. Which is the problem i have when i have it enabled. When i have the STA driver enabled i can't detect wireless networks. and when i type in sudo iwlist scan i get:


lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

vboxnet0  Interface doesn't support scanning.

wlan0     No scan results

i'm so confused right now i don't know what to do. So even though i can detect the wireless networks iwlist scan doesn't return anything

---

### Post by gresavage on 2010-11-21
okay nevermind i can't detect the wireless networks again. IDK WHAT'S GOING ON

---

