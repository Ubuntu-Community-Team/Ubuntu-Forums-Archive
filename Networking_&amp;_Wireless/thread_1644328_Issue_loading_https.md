---
title: "Issue loading https"
date: 2010-12-13
forum: Networking &amp; Wireless
---

### Post by onethirtythreeseven on 2010-12-13
This started yesterday.  I haven't made any recent changes.  I can't access any pages beginning with https.  It's just my computer because my girlfriend's laptop doesn't have any issues.  I'm using OpenDNS, but I have been for a long time and this is the first time this has ever happened.  I'm not using a router, I connect straight to the modem, which I've already reset.  I can't figure it out.  Can anybody help?  Here's some more info:

```
sean@lappy:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:22:19:e7:9c:96  
          inet addr:69.136.244.65  Bcast:69.136.245.255  Mask:255.255.254.0
          inet6 addr: fe80::222:19ff:fee7:9c96/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12858611 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4901734 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6820073966 (6.8 GB)  TX bytes:3041150286 (3.0 GB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:15000 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15000 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1174944 (1.1 MB)  TX bytes:1174944 (1.1 MB)

wlan0     Link encap:Ethernet  HWaddr 00:22:fb:31:68:40  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:441691 errors:0 dropped:0 overruns:0 frame:0
          TX packets:320621 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:548111133 (548.1 MB)  TX bytes:65225367 (65.2 MB)
```

```
sean@lappy:~$ telnet mail.google.com 443
Trying 72.14.204.19...
Trying 72.14.204.17...
Trying 72.14.204.83...
Trying 72.14.204.18...
telnet: Unable to connect to remote host: Connection timed out
sean@lappy:~$ telnet www.google.com 80
Trying 74.125.226.144...
Connected to www.l.google.com.
Escape character is '^]'.
^]

telnet> 

```

---

### Post by onethirtythreeseven on 2010-12-13
Bump.

---

