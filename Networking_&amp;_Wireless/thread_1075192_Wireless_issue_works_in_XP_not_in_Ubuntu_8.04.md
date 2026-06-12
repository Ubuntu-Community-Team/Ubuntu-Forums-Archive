---
title: "Wireless issue: works in XP not in Ubuntu 8.04"
date: 2009-02-20
forum: Networking &amp; Wireless
---

### Post by apmjoshi on 2009-02-20
Greetings,

I have an old ACER Travelmate 290 laptop which is a dual-boot machine with Windows XP and Ubuntu 8.04. Wireless 802.11b is built-in and there is a hardware switch on the side to enable/disable WiFi.

As far as wireless networking goes, I get the following results consistently:
a. wireless always works under Windows XP.
b. wireless never works if I boot directly into Ubuntu. Toggling the hardware switch has no effect.
c. if I boot into Windows first and then restart, but select Ubuntu upon restart, wireless works without any problems. I can disable wireless through the hardware switch and enable it again using the same switch

So my guess is that it is the sequence of driver loading under Ubuntu that is the issue and not compatibility of drivers. I am at work but can post diagnostics later on if required.

Any help or pointers for solving this long-standing frustration are most welcome.

Regards
Aniruddha

---

### Post by ProNux on 2009-02-20
How did you get your WLAN working in Ubuntu?  Did Ubuntu detected it directly or you compile the drivers yourself?  Did you use WINE?  I am not an Ubuntu expert, only my ideas...

---

### Post by apmjoshi on 2009-02-21
WLAN = wireless LAN? Strictly speaking it does not 'work' under Ubuntu. Whenever it does, the Windows XP leaves the Wireless connection up which Ubuntu can recognise and work with.

I did not compile any drivers, simply installed Ubuntu from the liveCD.

Regards
Andy

---

### Post by ProNux on 2009-02-21
Open the console and post the output of
```
ifconfig
```

---

### Post by apmjoshi on 2009-02-24
Hi ProNux,

Here is the output you asked for
```
andy@andy-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:02:3f:14:ba:22  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::202:3fff:fe14:ba22/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:345 errors:0 dropped:0 overruns:0 frame:0
          TX packets:90 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:29960 (29.2 KB)  TX bytes:10129 (9.8 KB)
          Interrupt:10 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:0c:f1:20:77:ab  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:10 Base address:0x8000 Memory:d0000000-d0000fff 

eth1:avahi Link encap:Ethernet  HWaddr 00:0c:f1:20:77:ab  
          inet addr:169.254.7.130  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:10 Base address:0x8000 Memory:d0000000-d0000fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1620 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1620 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:81000 (79.1 KB)  TX bytes:81000 (79.1 KB)
```

---

