---
title: "Intel NIC 82567LF-2 - intermittently losing connectivity"
date: 2009-05-22
forum: Networking &amp; Wireless
---

### Post by KhanCarne on 2009-05-22
Hey folks,

I have a Dell Studio XPS 435MT running 64bit Jaunty with a Intel 82567LF-2 NIC that will start dropping packets for stretches of several seconds before resuming normal operation.  The e1000e modules appears to be loading correctly.  I've tried several things:

1. /var/log/messages is clear of any suspicious entries for the NIC other than "eth0: No IPv6 routers present" (I'm using IPv4),
2. switched the network cables and ports on the switch,
3. flood pings to/from the problem child from/to another box on the switch shows stretches on dropped packets, with the time of these little vacations varying from a few seconds to until I get frustrated and ctrl-c (after a few minutes).
4. flood pings from one working machine to another don't show any dropped packets.
5. web searches are inundated with hits about the rather heinous kernel bug in e1000e from 2.6.27 that would clobber the firmware, but I'm running 2.7.28.

Does anybody have any ideas about other diagnostics I could run to track down this problem?

---

### Post by superprash2003 on 2009-05-22
could you post output of ifconfig from the terminal , could be an MTU related issue

---

### Post by KhanCarne on 2009-05-22
Here it is:

eth0      Link encap:Ethernet  HWaddr 00:24:e8:0c:41:08  
          inet addr:165.68.22.100  Bcast:165.68.22.255  Mask:255.255.255.0
          inet6 addr: fe80::224:e8ff:fe0c:4108/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4899481 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3693117 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2921261214 (2.9 GB)  TX bytes:338461665 (338.4 MB)
          Memory:fbbc0000-fbbe0000 

Thanks

---

### Post by superprash2003 on 2009-05-23
try disabling ipv6 [http://www.prash-babu.com/2009/01/how-to-disable-ipv6-in-linux-ubuntu-to.html](http://www.prash-babu.com/2009/01/how-to-disable-ipv6-in-linux-ubuntu-to.html)

---

