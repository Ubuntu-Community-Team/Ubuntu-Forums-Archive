---
title: "Broken ADSL/Modem router?"
date: 2009-10-18
forum: Networking &amp; Wireless
---

### Post by ajifans on 2009-10-18
I've got a used Netgear DG834GT, which I am unable to access through it's default access: [http://192.168.0.1](http://192.168.0.1)

Running ifconfig produces the following results:

```
eth0      Link encap:Ethernet  HWaddr 00:50:8d:d9:5d:c9  
          inet6 addr: fe80::250:8dff:fed9:5dc9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6657 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5562 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7450593 (7.4 MB)  TX bytes:883765 (883.7 KB)
          Interrupt:23 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:42 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2140 (2.1 KB)  TX bytes:2140 (2.1 KB)

```

If I run ipconfig in WinXP the Default Gateway line is blank.

I'm not behind a firewall, and I can swap the router out for another and it works just fine.
I've tried accessing the router with another machine using both Windows and Linux to no avail, and have also hard reset the router.

Is the router likely to be broken?

---

