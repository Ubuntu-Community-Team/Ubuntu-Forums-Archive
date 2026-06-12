---
title: "Can't enable wireless"
date: 2011-06-25
forum: Networking &amp; Wireless
---

### Post by thunderbirdje on 2011-06-25
Hello Everyone,

I've installed Ubuntu 11.04 on my (rather 'old') desktop.

I can surf the internet with a cable (LAN) connected. However I can't surf wireless because **I can't enable Enable Wireless** in the indicator applet. See [IMG]http://ubuntuforums.org/attachment.php?attachmentid=195932&stc=1&d=1309011768[/IMG]

**ifconfig** returns:

```
eth0      Link encap:Ethernet  HWaddr 00:11:09:f3:a3:c9  
          inet addr:192.168.178.23  Bcast:192.168.178.255  Mask:255.255.255.0
          inet6 addr: fe80::211:9ff:fef3:a3c9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6302 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5338 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6646877 (6.6 MB)  TX bytes:1031086 (1.0 MB)
          Interrupt:18 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1440 (1.4 KB)  TX bytes:1440 (1.4 KB)

```

However I've noticed that wlan0 is listed into the Netwerk tools. See [IMG]http://ubuntuforums.org/attachment.php?attachmentid=195933&stc=1&d=1309011768[/IMG] 

Hope someone can guide me :D

---

