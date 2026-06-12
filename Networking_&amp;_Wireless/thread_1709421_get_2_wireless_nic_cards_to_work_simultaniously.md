---
title: "get 2 wireless nic cards to work simultaniously"
date: 2011-03-18
forum: Networking &amp; Wireless
---

### Post by karthik_makam on 2011-03-18
hi 
i have 2 wireless cards one is inbuilt(intel pro/wireless 5300 AGV) and the other is an external card atheros ar5008 wireless network adapter when i do if config i get
wlan0     Link encap:Ethernet  HWaddr 00:21:6a:7b:e7:20  
          inet addr:192.168.5.206  Bcast:192.168.5.255  Mask:255.255.255.0
          inet6 addr: fe80::221:6aff:fe7b:e720/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14850 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13333 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12356461 (12.3 MB)  TX bytes:4751223 (4.7 MB)

wlan1     Link encap:Ethernet  HWaddr 00:17:9a:45:9a:b6  
          inet addr:192.168.5.204  Bcast:192.168.5.255  Mask:255.255.255.0
          inet6 addr: fe80::217:9aff:fe45:9ab6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:61 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7638 (7.6 KB)  TX bytes:8165 (8.1 KB)
i know that both are detected but when i use wireshark i find that only one of the interface is active(i.e exchanging packets) the other is idle

can i get both the cards to work meaning transmit and receive packets simultaneously

thanks in advance

---

