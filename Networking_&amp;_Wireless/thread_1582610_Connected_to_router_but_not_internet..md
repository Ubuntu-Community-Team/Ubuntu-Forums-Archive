---
title: "Connected to router but not internet."
date: 2010-09-26
forum: Networking &amp; Wireless
---

### Post by sandbag the great on 2010-09-26
Hello, I am nub at puters so please treat me as such.

I am connected to my wireless network but can't connect to the internet. I have searched the ubuntu forums for solutions but none seem to work for me.

Can anyone give me advice or direction please? 

I can post terminal outputs if required (I know that much).

---

### Post by wojox on 2010-09-26
What does this tell us?


```
ping -c 5 www.google.com
```

```
ifconfig
```

---

### Post by sandbag the great on 2010-09-26
> **wojox said:**
> ping -c 5 [www.google.com](www.google.com)

```
 
ping: unknown host www.google.com 

```

> **WOJOX said:**
> ifconfig

```
 eth0      Link encap:Ethernet  HWaddr 00:21:85:08:0d:7c  
          UP BROADCAST MULTICAST  MTU:1492  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:251 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:404 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:404 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:31800 (31.8 KB)  TX bytes:31800 (31.8 KB) 

ra0       Link encap:Ethernet  HWaddr 00:1f:1f:36:9e:49  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0 
          inet6 addr: fe80::21f:1fff:fe36:9e49/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:51837 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:260 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:6394568 (6.3 MB)  TX bytes:60996 (60.9 KB) 
```

---

### Post by wojox on 2010-09-26
How about:

```
iwconfig
```

---

### Post by Iowan on 2010-09-26
Results of **route -n** might also be useful.

---

### Post by sandbag the great on 2010-09-27
> **wojox said:**
> iwconfig

```
 lo        no wireless extensions. 

eth0      no wireless extensions. 

ra0       RT2870 Wireless  ESSID:"23 Hazel Close"  Nickname:"RT2870STA" 
          Mode:Ad-Hoc  Frequency=2.462 GHz  Cell: DE:4C:09:DD:07:99   
          Bit Rate=11 Mb/s   
          RTS thr:off   Fragment thr:off 
          Link Quality=48/100  Signal level:-90 dBm  Noise level:-97 dBm 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

pan0      no wireless extensions. 
```

route -n 

```
 Kernel IP routing table 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
10.42.43.0      0.0.0.0         255.255.255.0   U     2      0        0 ra0 
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 ra0 
```

---

### Post by Iowan on 2010-09-27
Hmmm... :-k No gateway listed. Non-local traffic doesn't know where to go. I'd have thought the router would provide that information, but you should be able to add it via NM.

---

### Post by sandbag the great on 2010-09-28
Anyone got any thoughts on this.

I've just re-installed 9.04 and I'm still getting the same problem!

---

### Post by Iowan on 2010-09-28
Same results from **ifconfig -a** and **route -n**?

---

