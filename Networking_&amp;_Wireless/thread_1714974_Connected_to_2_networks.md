---
title: "Connected to 2 networks"
date: 2011-03-26
forum: Networking &amp; Wireless
---

### Post by m666 on 2011-03-26
I'm connected to 2 networks (ethernet and wifi). How do I know  which network  I get internet from? Is it possible to bridge interfaces to speed up transfers? If not, maybe to set up somehow priorities? I could monitor network traffic using 'conky' but I like to keep my desktop clean. Is there any command line conky-like tool? I mean something like 'top' command but showing network activity instead of processes.



```
$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1b:38:0e:02:24  
          inet addr:192.168.0.113  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fe0e:224/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:492337 errors:0 dropped:0 overruns:0 frame:0
          TX packets:544889 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:125087688 (125.0 MB)  TX bytes:355549100 (355.5 MB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:664 (664.0 B)  TX bytes:664 (664.0 B)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1c:bf:98:8d:12  
          inet addr:192.168.1.67  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:bfff:fe98:8d12/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38607 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27770 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:35099866 (35.0 MB)  TX bytes:3424170 (3.4 MB)
```

---

