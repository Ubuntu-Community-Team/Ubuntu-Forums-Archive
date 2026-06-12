---
title: "Ethernet Port not recognized"
date: 2011-07-27
forum: Networking &amp; Wireless
---

### Post by littlebird on 2011-07-27
I am running 11.04 on a Dell Inspiron 1501 (the first gen.).  I was using my Ethernet port to connect to the internet until about two weeks ago - suddenly the system no longer recognised that port even existed and just kicked me offline.  I am able to get online now with a wireless card (replaced the broadcom card, that was a whole different can of worms...).  

Does anyone have any ideas why my system is unable to connect with the Ethernet port?  If I plug in the cable nothing happens.  Any help would be appreciated.

---

### Post by 2F4U on 2011-07-27
Maybe a hardware problem? What happens if you type ifconfig in a terminal? Do you see the network interface eth0?

---

### Post by littlebird on 2011-07-28
> **2F4U said:**
> Maybe a hardware problem? What happens if you type ifconfig in a terminal? Do you see the network interface eth0?


This is what I get: 
lo        Link encap:Local Loopback  
          inet addr:               Mask:
          inet6 addr:              Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:48 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3880 (3.8 KB)  TX bytes:3880 (3.8 KB)

wlan1     Link encap:Ethernet  HWaddr 00:1f:3b:a7:19:5d  
          inet addr:                 Bcast:                 Mask:
          inet6 addr:                         Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1126 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1209 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:861322 (861.3 KB)  TX bytes:263218 (263.2 KB)

It looks like there is some sort of ethernet recognition?  I am not very proficient with command lines.

---

### Post by fallfallfall on 2012-10-09
I have this same problem. Did you ever figure out what was wrong?

---

### Post by Elfy on 2012-10-11
Rather than resurrect an old thread start a new one.

Give as much information as you can. See the Help People Help You link in my sig.

Closed.

---

