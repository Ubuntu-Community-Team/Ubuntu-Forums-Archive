---
title: "Just installed WLAN Router ZyXEL 660HN. Cannot attach big files (1.7 Mb) to emails"
date: 2010-01-15
forum: Networking &amp; Wireless
---

### Post by eckart.hars on 2010-01-15
Hi,

Does anybody know what to do? Internet works fine except for that problem. I can attach files of 33kb in web-based email service (Gmail) but no big ones. 

yours,

Eckart.

---

### Post by pricetech on 2010-01-15
Any chance your email provider has a small limit on the size of attachments ??  I know it sounds ridiculous, but a meg used to be the limit with some of them.

---

### Post by superprash2003 on 2010-01-15
this could be an MTU problem.. post output of **ifconfig** from the terminal

---

### Post by eckart.hars on 2010-01-16
Hello, I encounter the same problems on other email providers. ifconfig shows the following. Does this give a clue? I am just a total beginner on ubuntu ...

eth0      Link encap:Ethernet  HWaddr 00:16:36:48:4c:90  
          inet addr:192.168.1.33  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fe48:4c90/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17719 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17891 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10103944 (9.6 MB)  TX bytes:3725653 (3.5 MB)
          Interrupt:16 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1634 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1634 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:81700 (79.7 KB)  TX bytes:81700 (79.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:13:02:14:72:c1  
          inet addr:192.168.1.34  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:2ff:fe14:72c1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1410 (1.3 KB)  TX bytes:7455 (7.2 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-02-14-72-C1-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

