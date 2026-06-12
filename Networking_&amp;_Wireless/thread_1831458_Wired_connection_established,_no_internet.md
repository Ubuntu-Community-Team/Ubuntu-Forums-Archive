---
title: "Wired connection established, no internet"
date: 2011-08-23
forum: Networking &amp; Wireless
---

### Post by moonsal on 2011-08-23
Ok, after fiddling with this wet54g bridge for forever I had no luck with DHCP at all... So I went into NM and switched from DHCP to manual and entered in 192.168.1.226 for my IP, 255.255.255.0 for netmask and 192.168.1.1 for gateway (my router IP).. Now I can access everything in my own network and ping everything as well but when I try to ping lets say [www.ubuntuforums.org](www.ubuntuforums.org) it comes back as unknown host?? I can switch to just about any IP that I want and I can still access my network.. Even leave the bridge on DHCP and just set up my NM to manual and can still access the network but NOTHING outside???

I have changed my bridge from DHCP to static and back many times (even resetting it and hooking it back up to the router as well just to be sure).. I looked up this morning at my DHCP client table for my router and it showed the system was given an IP od 192.168.1.111 so I went ahead and set my bridge to that ip and also changed my Manual connection to the same... Still, just network and no internet??? Anyone have any Ideas or solutions... I know it can be done, I'm just overlooking something.....

In much need of some help... Thanks

---

### Post by moonsal on 2011-08-23
```
n1x4@MyBox:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:76:13:16:44  
          inet addr:192.168.1.111  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:76ff:fe13:1644/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1641 (1.6 KB)  TX bytes:8273 (8.2 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:561 errors:0 dropped:0 overruns:0 frame:0
          TX packets:561 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:48898 (48.8 KB)  TX bytes:48898 (48.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:12:17:9d:99:f2  
          inet6 addr: fe80::212:17ff:fe9d:99f2/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:835222 errors:0 dropped:0 overruns:0 frame:0
          TX packets:464858 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1066788374 (1.0 GB)  TX bytes:46341936 (46.3 MB)

```

```
n1x4@MyBox:~$ ip route
192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.111  metric 1 
169.254.0.0/16 dev eth0  scope link  metric 1000 
default via 192.168.1.1 dev eth0  proto static
```

---

### Post by Iowan on 2011-08-23
> **moonsal said:**
> ...but when I try to ping lets say [www.ubuntuforums.org](www.ubuntuforums.org) it comes back as unknown host??  Can you ping internet site by IP address (eg. 74.125.225.52)?
If so, you may need to set up the DNS address in NM.

---

### Post by moonsal on 2011-08-24
I'll be a SOB..... It works now!!! I have been working on this for literally MONTHS!!!!!!!!!!! Thank you for your help maaan... :guitar::guitar::guitar::guitar::guitar::guitar::guitar::guitar:

---

