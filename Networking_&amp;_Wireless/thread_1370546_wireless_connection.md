---
title: "wireless connection"
date: 2010-01-02
forum: Networking &amp; Wireless
---

### Post by spiky001 on 2010-01-02
Hi i'm having a wireless connection problem, i put a netgear wg111 in my pc, which has the internet connection i now want to send it to laptop, net connection is via mobile usb ddongle all good there eth0 works fine to laptop, I can see neighbour network so must be working. the problem is laptop cant see it (XP or UBUNTU) made a network name set wireless shared

```
spiky@server:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:30:1b:ae:9f:28  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::230:1bff:feae:9f28/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16263 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27439 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3050240 (3.0 MB)  TX bytes:13367715 (13.3 MB)
          Interrupt:21 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:92.40.39.71  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1440  Metric:1
          RX packets:455 errors:0 dropped:0 overruns:0 frame:0
          TX packets:394 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:411316 (411.3 KB)  TX bytes:40697 (40.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:22:3f:ed:80:14  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-22-3F-ED-80-14-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

my ifconfig     if more info needed will get

any ideas

---

### Post by spiky001 on 2010-01-02
bump

---

### Post by spiky001 on 2010-01-02
any help plz have installed ndiswrapper & driver still no luck

---

