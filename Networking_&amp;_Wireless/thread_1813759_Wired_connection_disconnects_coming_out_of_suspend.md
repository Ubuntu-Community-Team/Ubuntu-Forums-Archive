---
title: "Wired connection disconnects coming out of suspend"
date: 2011-07-28
forum: Networking &amp; Wireless
---

### Post by AdamBradley on 2011-07-28
Hi,

I hope someone can help me with this problem - I'm a new Ubuntu user and am thoroughly confused.

I have both a wired (eth0) and wireless (eth1) connection on my Compaq laptop running Natty 11.04. When I start up from scratch, or restart the machine, the wired connection connects and becomes my primary connection.

But when I bring the machine out of suspend, the wifi connects and the wired doesn't. And if I try and use the wired connection, it says "Wired network disconnected" even though it isn't.

ifconfig produces this:


eth0      Link encap:Ethernet  HWaddr 60:eb:69:48:16:b2  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:152158 errors:0 dropped:0 overruns:0 frame:0
          TX packets:133220 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:34419173 (34.4 MB)  TX bytes:15372914 (15.3 MB)
          Interrupt:42 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:26:82:ba:88:97  
          inet addr:192.168.2.13  Bcast:192.168.2.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:745105 errors:0 dropped:0 overruns:0 frame:1990723
          TX packets:558148 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:596022367 (596.0 MB)  TX bytes:67409660 (67.4 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:992 errors:0 dropped:0 overruns:0 frame:0
          TX packets:992 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:50844 (50.8 KB)  TX bytes:50844 (50.8 KB)


Help! It's not the worst thing ever, since I can still connect wirelessly, but I'd like to know what's going wrong.

Thanks

---

