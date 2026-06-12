---
title: "networking 2 Ubuntu boxes with a crossover cable"
date: 2009-08-16
forum: Networking &amp; Wireless
---

### Post by rockerphil on 2009-08-16
ok, the title pretty well says it, but here's a quick rundown. i want to network my two Ubuntu boxes using a crossover cable (i'm too broke to buy a router or a switch). i already have the crossover cable made, i just need some help with the details. the two machines are both a bit older, so i did a minimal install from an 8.04 CLI install then built the GUI using Fluxbox as the WM, so i'd prefer to do this through either a command prompt or by manually editing the config files. also, here is the ifconfig for the machine with 2 Ethernet cards.

```
eth0      Link encap:Ethernet  HWaddr 00:14:d1:11:35:5b  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:d1ff:fe11:355b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:107361 errors:0 dropped:0 overruns:0 frame:0
          TX packets:139283 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23132961 (22.0 MB)  TX bytes:157963668 (150.6 MB)
          Interrupt:11 Base address:0x8c00 

eth1      Link encap:Ethernet  HWaddr 00:c0:f0:2b:c4:29  
          inet6 addr: fe80::2c0:f0ff:fe2b:c429/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:441 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:149238 (145.7 KB)
          Interrupt:3 Base address:0xdf80 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:333 errors:0 dropped:0 overruns:0 frame:0
          TX packets:333 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14352 (14.0 KB)  TX bytes:14352 (14.0 KB)
```

if any more information is required feel free to ask. any help is appreciated and much thanks in advance,

Phil

---

### Post by rockerphil on 2009-08-17
anyone?

---

### Post by Iowan on 2009-08-17
I skipped 8.04 and 8.10. A couple of How-To's on static addresses:
[For 8.10]("http://ubuntuforums.org/showthread.php?t=974382")
[http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html]("http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html")
[Another 8.10]("http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html")

---

