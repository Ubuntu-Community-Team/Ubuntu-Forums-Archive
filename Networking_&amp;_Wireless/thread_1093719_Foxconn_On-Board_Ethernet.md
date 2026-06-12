---
title: "Foxconn On-Board Ethernet"
date: 2009-03-11
forum: Networking &amp; Wireless
---

### Post by gamgee911 on 2009-03-11
Hey everybody.

Curious if someone can point me in the right direction.  I have a 661MX Plus Foxconn Motherboard.  The ethernet is recognized and it is an option along with my pci wifi nic.  The ethernet will not connect to my wired network (confirmed working with other computer) but the wireless connects fine.  Here is the output of ifconfig.

```
samuelgrund@Lilija:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:11:95:93:7f:56  
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::211:95ff:fe93:7f56/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:2162 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1704 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2775098 (2.7 MB)  TX bytes:225012 (225.0 KB)

eth0      Link encap:Ethernet  HWaddr 00:1c:25:36:25:ad  
          inet6 addr: fe80::21c:25ff:fe36:25ad/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2014 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:123611 (123.6 KB)  TX bytes:1494 (1.4 KB)
          Interrupt:19 Base address:0xe800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:376 (376.0 B)  TX bytes:376 (376.0 B)

wifi0     Link encap:UNSPEC  HWaddr 00-11-95-93-7F-56-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21269 errors:0 dropped:0 overruns:0 frame:12313
          TX packets:1914 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:6696561 (6.6 MB)  TX bytes:312502 (312.5 KB)
          Interrupt:19 

```

Any help is greatly appreciated, thanks guys!

---

