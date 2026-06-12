---
title: "network manager showing a &quot;network problem&quot; icon when the networking is healthy"
date: 2009-05-20
forum: Networking &amp; Wireless
---

### Post by bkline on 2009-05-20
I just upgraded Ubuntu 8.04 to 9.04 and all of a sudden the little icon for the Network Manager applet is showing a red "X" (actually, it's a white "X" on a red background), even though both the wired and the wireless connection are working fine.  I mean, I'm happy that the networking is healthy, but I'd be even happier if NM would stop crying "wolf"; it's sort of like having the oil light stuck on in your car.  Did Jaunty break something?  Here's the output of ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 00:1f:c6:4b:94:d3  
          inet addr:66.92.147.62  Bcast:66.92.147.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:c6ff:fe4b:94d3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3407167 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2286078 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3894748024 (3.8 GB)  TX bytes:262482690 (262.4 MB)
          Interrupt:254 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:26 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1680 (1.6 KB)  TX bytes:1680 (1.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:44:b0:2b:ea  
          inet addr:192.168.0.104  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:44ff:feb0:2bea/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:321061 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8530 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:104372651 (104.3 MB)  TX bytes:2636082 (2.6 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-16-44-B0-2B-EA-62-65-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

---

### Post by Iowan on 2009-05-20
Did you configure interfaces via Network Manager - or via /etc/network/interfaces?  The latter would explain the problem.

---

### Post by bkline on 2009-05-22
> **Iowan said:**
> Did you configure interfaces via Network Manager - or via /etc/network/interfaces?  The latter would explain the problem.

I haven't ever edited /etc/network/interfaces.  Even if I had, what purpose would be served by having Network Manager display an icon which indicates that the network has a problem when it doesn't?

---

### Post by Iowan on 2009-05-22
Network Manager doesn't use */etc/network/interfaces* file.  If the interface is set up there, it may still work, but NM will not know about it... and might report the interface as not working (or at least "not managed").

---

### Post by bkline on 2009-05-22
> **Iowan said:**
> Network Manager doesn't use */etc/network/interfaces* file.  If the interface is set up there, it may still work, but NM will not know about it... and might report the interface as not working (or at least "not managed").

I see.  So, no one but me thinks it's a problem that NM is displaying an icon indicating a non-existent problem?  I mean, wouldn't you want the oil light in your car to light up only when you needed to add oil?

---

### Post by Iowan on 2009-05-22
I'm not suggesting it - but you could remove Network Manager. That would be analogous to taking out the light bulb (or disconnecting the sensor that might be stuck). That'd be the quick/dirty fix.  The "right" way would be to find why Network Manager thinks there is a problem. Your */etc/network/interfaces* file should contain only: ```
auto lo
iface lo inet loopback
```

---

### Post by bkline on 2009-05-22
> **Iowan said:**
> ....  The "right" way would be to find why Network Manager thinks there is a problem. Your */etc/network/interfaces* file should contain only: ....

Thanks for the suggestion, but when I tried it (removing everything but those two lines from *interfaces* in order to let NM take over) NM wouldn't let me set up the static IP for my wired connection, which pretty much hosed the machine for any useful work.  So I'll fall back on your plan B suggestion (remove NM).

Cheers,
Bob

---

