---
title: "no eth0 option"
date: 2009-10-02
forum: Networking &amp; Wireless
---

### Post by vielmaj on 2009-10-02
When I run ifconfig I get the following output

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:15:af:dd:8e:24  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-15-AF-DD-8E-24-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

I have no eth0 option.  How do I fixed this so I can use my eth0 connection on my laptop?

---

### Post by crolanx on 2009-10-03
Maybe eth0 is down...

You could try to use ```
ifconfig -a
``` to show all interfaces, even those which are down.

---

### Post by t0mppa on 2009-10-03
Just run **lshw -C network**, it will show the status of you network interfaces and their drivers. Usually these are driver issues or then disabled interfaces.

---

### Post by Iowan on 2009-10-04
Check **ifconfig -a**. That will show all interfaces - even if down.

---

