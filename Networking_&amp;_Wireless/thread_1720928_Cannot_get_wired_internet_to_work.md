---
title: "Cannot get wired internet to work"
date: 2011-04-03
forum: Networking &amp; Wireless
---

### Post by megamark on 2011-04-03
I posted this in general help and realized it probably belongs here. I no longer have a Auto eth0 connection. I am running 10.04 and have not done any major changes. Here is my ifconfig -a:

=========================================================

eth0      Link encap:Ethernet  HWaddr 00:1a:a0:97:65:a9  
          BROADCAST MULTICAST  MTU:1492  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:fdfc0000-fdfe0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:131343 errors:0 dropped:0 overruns:0 frame:0
          TX packets:131343 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6574576 (6.5 MB)  TX bytes:6574576 (6.5 MB)

wlan0     Link encap:Ethernet  HWaddr 00:1d:60:13:d2:94  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

===========================================================

I would really appreciate some help.

---

### Post by lytithwyn on 2011-05-03
What happens if you run this from the command line?

```
sudo /sbin/dhclient eth0
```

---

