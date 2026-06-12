---
title: "WICD HP Pavillion Dv6000 Wireless Card"
date: 2009-11-18
forum: Networking &amp; Wireless
---

### Post by Swen702 on 2009-11-18
Okay well, im not new to the whole forum world of the internet, but i am, however, very new to the world of Ubuntu.

Here's the story, I had a windows 7 eval copy and refused to go back to vista and xp. microshaft really has a way with marketing garbage OS's. So ive spent the last 5 or so hours trying to find help on why my wireless internet doesnt work.

Like the title above i have an HP PavillionDv6000 (the wireless switch is on! i saw the other thread) and have already installed WICD network manager. for 5 minutes i was able to see my internet as well as neighboring networks. Now, nothing works unless im hardwired into the router through my ethernet.

i know theres scripts to type into terminal that could help diagnose the problem from what i have been seeing on the forums but have no idea which one to type or what to do. help?

-thanks in advance,
swen.

---

### Post by eremyja on 2009-11-18
run this to make sure it still sees it:
```
lspci -v | less
```

if you see it then run this to see if its working

```

ifconfig

```

---

### Post by Swen702 on 2009-11-18
heres what came back. it was recognized with the first command
and then this came back with ifconfig.


eth0      Link encap:Ethernet  HWaddr 00:1b:24:ce:7a:e8  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:24ff:fece:7ae8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1788 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2021 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1425725 (1.4 MB)  TX bytes:405051 (405.0 KB)
          Interrupt:27 Base address:0x2000 

eth3      Link encap:Ethernet  HWaddr 00:1a:73:ba:c8:1b  
          inet6 addr: fe80::21a:73ff:feba:c81b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9320 (9.3 KB)  TX bytes:9320 (9.3 KB)

---

