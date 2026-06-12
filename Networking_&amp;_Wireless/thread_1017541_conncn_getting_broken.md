---
title: "conncn getting broken"
date: 2008-12-21
forum: Networking &amp; Wireless
---

### Post by akh00 on 2008-12-21
I'm from India and am using a 2mbps broadband connection. I'm using UBuntu 8.04 and have set up my connection without problems. But my problem is that the connection sometimes breaks suddenly without warning.  I can say that there's no problem with my ISP because I use XP jn dual boot and have no problems there. Also, the speed in linux is sometimes dreadfully slow and sometimes lighting fast, while in XP it's always fast (i.e. the max of what my conncn offers).

Can someone please tell me how to solve these two problems? thanks a lot.

---

### Post by superprash2003 on 2008-12-21
post ifconfig output from the terminal.. do you use a dialer in windows to connect to the internet or does the internet work as soon as you switch on the modem?do you mean downloading speed or browsing speed?

---

### Post by akh00 on 2008-12-21
here's my ifconfig. and yes, i use a dialer to connect in windows. and by speeds i mean browsing speeds, altho the few downloads i tried were slow too, compared to XP

```
eth0      Link encap:Ethernet  HWaddr 00:16:76:33:d2:70  
          inet6 addr: fe80::216:76ff:fe33:d270/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:804 errors:0 dropped:0 overruns:0 frame:0
          TX packets:862 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:756836 (739.0 KB)  TX bytes:121084 (118.2 KB)
          Interrupt:20 Base address:0xde00 

lo        Link encap:Local Loopback  
          inet addr:******  Mask:******
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2574 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2574 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:128700 (125.6 KB)  TX bytes:128700 (125.6 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:******  P-t-P:*******  Mask:*******
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:786 errors:0 dropped:0 overruns:0 frame:0
          TX packets:840 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:738306 (721.0 KB)  TX bytes:101116 (98.7 KB)
```

---

### Post by akh00 on 2008-12-22
sorry for bumping but i really need to get this problem solved!

---

### Post by superprash2003 on 2008-12-23
your eth0 doesnt seem to be getting an ip from your router.. post output of ping 192.168.1.1 from your termina

---

