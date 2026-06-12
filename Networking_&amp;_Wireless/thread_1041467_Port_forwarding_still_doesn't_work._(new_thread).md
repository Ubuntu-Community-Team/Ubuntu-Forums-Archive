---
title: "Port forwarding still doesn't work. (new thread)"
date: 2009-01-16
forum: Networking &amp; Wireless
---

### Post by unused_bagels on 2009-01-16
I have ubuntu Heron, a static IP (from the router, so I can still use NM), and ports 57000-57009 forwarded to my IP address from the router and the modem.  What am I doing wrong? I try the port on canyouseeme and it's still closed!

if config
```
eth0      Link encap:Ethernet  HWaddr 00:1d:60:c1:69:eb  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:60ff:fec1:69eb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:63032 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29616 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:67158784 (64.0 MB)  TX bytes:2901626 (2.7 MB)
          Interrupt:253 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2084 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2084 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:104200 (101.7 KB)  TX bytes:104200 (101.7 KB)

```
router:
[IMG]http://i43.tinypic.com/2zoj5ax.png[/IMG]
(they are called Ktor because I haven't bothered changing it yet, but those are the BT ports I intend to use.)

---

