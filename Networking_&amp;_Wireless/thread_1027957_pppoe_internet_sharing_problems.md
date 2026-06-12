---
title: "pppoe internet sharing problems"
date: 2009-01-01
forum: Networking &amp; Wireless
---

### Post by peuplarchie on 2009-01-01
Good day to you all,
               I'm new to Linux and i'm very impress with it, wondering how come I didn't do this earlier in my life...

               I have 4 Ubuntu 8.10 machine on a network along 2 windows.
               No problem sharing files, but the internet connection  don't want to work on other pc that the one it setup on.

               it's been 3 days not looking on the net and testing many thing, same result.

Thanks !

---

### Post by cabbiinc on 2009-01-01
> **peuplarchie said:**
> Good day to you all,
               I'm new to Linux and i'm very impress with it, wondering how come I didn't do this earlier in my life...

               I have 4 Ubuntu 8.10 machine on a network along 2 windows.
               No problem sharing files, but the internet connection  don't want to work on other pc that the one it setup on.

               it's been 3 days not looking on the net and testing many thing, same result.

Thanks !

Is your problem on a Windows PC or a Linux PC? What are you wired or wireless?

---

### Post by peuplarchie on 2009-01-01
Ubuntu 8.10
Wired

---

### Post by peuplarchie on 2009-01-01
static IP

---

### Post by peuplarchie on 2009-01-01
eth0      Link encap:Ethernet  HWaddr 00:08:74:4f:12:a8  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::208:74ff:fe4f:12a8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3340 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2758 errors:0 dropped:0 overruns:0 carrier:0
          collisions:51 txqueuelen:10 
          RX bytes:2219844 (2.2 MB)  TX bytes:554347 (554.3 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:82 errors:0 dropped:0 overruns:0 frame:0
          TX packets:82 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6432 (6.4 KB)  TX bytes:6432 (6.4 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:192.197.166.24  P-t-P:192.197.166.6  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:3170 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2711 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:2136595 (2.1 MB)  TX bytes:492944 (492.9 KB)

---

### Post by cabbiinc on 2009-01-01
Ubuntu 8.10 wired to a router or through another computer?

---

### Post by peuplarchie on 2009-01-02
hub

---

