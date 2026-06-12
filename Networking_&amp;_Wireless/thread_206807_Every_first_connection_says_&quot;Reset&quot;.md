---
title: "Every first connection says &quot;Reset&quot;"
date: 2006-06-30
forum: Networking &amp; Wireless
---

### Post by joncheyne on 2006-06-30
Hi

Connected via broadband, been stable for a year now.

recently, when I fire up, say firefox or epiph, it gives me a browser error page saying "The connection to the server was reset while the page was loading."

When I click retry it works.

per site, not once per session. Same with all networks apps - even updates - just do a retry and it connects

Sound like DNS based problem :confused: maybe?

---

### Post by thingy on 2006-06-30
1. Please provide the output from:

route -n
ifconfig

2. Please try a different browser to see if its the same issue

3. See this thread:

[http://www.ubuntuforums.org/showthread.php?t=160615&highlight=connection+server+reset+page+loading](http://www.ubuntuforums.org/showthread.php?t=160615&highlight=connection+server+reset+page+loading)

The user in that thread did a router firmware update which resolved the problem for them. Does rebooting the router help the problem?


jin

---

### Post by joncheyne on 2006-06-30
[QUOTE=thingy]1. Please provide the output from:

route -n
ifconfig
[FONT="Courier New"]
 route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.31.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
192.168.121.0   0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
0.0.0.0         192.168.2.1     128.0.0.0       UG    0      0        0 eth0
128.0.0.0       192.168.2.1     128.0.0.0       UG    0      0        0 eth0
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0
jon@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:10:DC:FE:45:8B
          inet addr:192.168.2.5  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::210:dcff:fefe:458b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32932 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27546 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:43646309 (41.6 MiB)  TX bytes:3456892 (3.2 MiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:31396 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31396 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:7392617 (7.0 MiB)  TX bytes:7392617 (7.0 MiB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01
          inet addr:192.168.121.1  Bcast:192.168.121.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:59 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08
          inet addr:192.168.31.1  Bcast:192.168.31.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:59 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)[/FONT]

---

### Post by joncheyne on 2006-06-30
All browsers, plus synaptic and Gaim.

Tried a reset, same.

---

### Post by thingy on 2006-06-30
I'm not a networking expert, but what are these two lines about:

> 0.0.0.0 192.168.2.1 128.0.0.0 UG 0 0 0 eth0
128.0.0.0 192.168.2.1 128.0.0.0 UG 0 0 0 eth0

I don't think those should be there!

---

### Post by joncheyne on 2006-06-30
[QUOTE=thingy]I'm not a networking expert, but what are these two lines about:[/QUOTE]

No idea, not put there by me, thats for sure!

---

### Post by joncheyne on 2006-07-09
> **thingy said:**
> I'm not a networking expert, but what are these two lines about:



I don't think those should be there!

Hi again - still not tracked this down.

But, it is not the router as the laptop works. It is not the hardward as XP on Vmware works without a hitch. It is just my dapper that has broken.

Tried changing the dns to the isp, all that stuff. No joy.

the 128 netmask is related to ipv6 in some way?

---

### Post by joncheyne on 2006-07-09
Fixed. Uninstalled SWAN. ho hum

---

