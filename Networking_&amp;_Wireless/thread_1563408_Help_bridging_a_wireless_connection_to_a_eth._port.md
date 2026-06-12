---
title: "Help bridging a wireless connection to a eth. port"
date: 2010-08-29
forum: Networking &amp; Wireless
---

### Post by n2o-Gr55 on 2010-08-29
Hi all, i am trying to use my laptop (running Ubuntu) to take the connected wireless network to allow a separate computer (win7) to be wired to the Ethernet port and be connected to the Internet.

To reiterate,

I want to bridge my Ethernet and wireless connections so that a computer connected can use the Internet.


Modem---(wireless)---> Ubuntu Laptop---(Ethernet port)--- Win7 Desktop


Bonus: +1 cookie if you get me on the right track to a static IP. (I failed last time XD, and... the time before that ](*,)) Network bridge more important though. ;) 

--Additional info--
etc/network/interfaces file contents

```
auto lo
iface lo inet loopback
```ifconfig results

```
eth0      Link encap:Ethernet  HWaddr 00:16:d4:36:70:01  
          inet6 addr: fe80::216:d4ff:fe36:7001/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1022 errors:0 dropped:0 overruns:0 frame:0
          TX packets:173 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:84792 (84.7 KB)  TX bytes:43960 (43.9 KB)

eth1      Link encap:Ethernet  HWaddr 00:14:a5:ba:ed:42  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::214:a5ff:feba:ed42/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32867 errors:0 dropped:0 overruns:0 frame:29378
          TX packets:13939 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10973821 (10.9 MB)  TX bytes:2045200 (2.0 MB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4300 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4300 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1055286 (1.0 MB)  TX bytes:1055286 (1.0 MB)


```Any help would be appreciated.
Thanks, n2o-Gr55

---

### Post by Iowan on 2010-08-29
[This]("https://help.ubuntu.com/community/Internet/ConnectionSharing") help page *might* be useful.

Network Manager has an option for configuring a static address - it didn't work for you?

---

### Post by n2o-Gr55 on 2010-08-29
Wow, search fail on my part. Thanks for the help    	Iowan o.O

---

