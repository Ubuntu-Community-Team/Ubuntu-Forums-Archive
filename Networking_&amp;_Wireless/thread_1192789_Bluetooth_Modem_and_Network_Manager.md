---
title: "Bluetooth Modem and Network Manager"
date: 2009-06-20
forum: Networking &amp; Wireless
---

### Post by pratiks19 on 2009-06-20
The network manager in jaunty is not recognizing mobile broadband connection made using wvdial via bluetooth.
Due to this, I'm unable to use pidgin. 

I had no issues regarding the same connection in interpid.

ifconfig output (for reference):

> 
pratik@pratik-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:68:6b:95:6d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:250 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4302 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4302 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:262862 (262.8 KB)  TX bytes:262862 (262.8 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:117.98.41.195  P-t-P:192.168.100.101  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:34895 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45897 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:16938746 (16.9 MB)  TX bytes:26718813 (26.7 MB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:5c:4d:7e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-5C-4D-7E-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



Please help me with this.

---

