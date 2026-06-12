---
title: "TUN inteface gone missing!"
date: 2009-04-14
forum: Networking &amp; Wireless
---

### Post by thespinesplitter on 2009-04-14
as the title says, yesterday i had an IPv6 tunnel going and now the interface has gone missing.

can someone tell me how can i go about setting up my tun interface to work with tspc so i have a IPv6 tunnel again?

ifconfig -a:
```
eth0      Link encap:Ethernet  HWaddr 00:c0:9f:b3:05:94  

          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0

          inet6 addr: fe80::2c0:9fff:feb3:594/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:2208 errors:0 dropped:0 overruns:0 frame:0

          TX packets:2075 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:400074 (390.6 KB)  TX bytes:189442 (185.0 KB)

          Interrupt:11 Base address:0xa000 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:1698 errors:0 dropped:0 overruns:0 frame:0

          TX packets:1698 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:84900 (82.9 KB)  TX bytes:84900 (82.9 KB)



wlan0     Link encap:Ethernet  HWaddr 00:90:4b:f7:ff:ba  

          BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



wmaster0  Link encap:UNSPEC  HWaddr 00-90-4B-F7-FF-BA-00-00-00-00-00-00-00-00-00-00  

          BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

thanks in advance.

---

