---
title: "Gateway will not connect to wireless"
date: 2012-05-11
forum: Networking &amp; Wireless
---

### Post by WebDevoNick on 2012-05-11
I just got a new job and for some odd reason, my Gateway MT6459 will not connect (both wireless and hardline), yet everywhere else it will connect. There are 2 connections that I could potentially connect to one is WPA Personal, the other is WEP.

Computer Specs:
Gateway MT6459
Ubuntu 12.04LTS

```

ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:e0:b8:d4:5a:8d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2608 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2608 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:229940 (229.9 KB)  TX bytes:229940 (229.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:c0:a8:ec:19:87  
          inet addr:192.168.2.6  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:a8ff:feec:1987/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:116814 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68586 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:163094203 (163.0 MB)  TX bytes:7559038 (7.5 MB)

-------------------

iwconfig

lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"NickBelangerRA"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 08:86:3B:30:19:92   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-37 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:202  Invalid misc:5235   Missed beacon:0

eth0      no wireless extensions.

---------

```
If you need anything else let me know! I need this to work so I can do my job.

---

