---
title: "packet loss over wireless after upgrade"
date: 2009-04-29
forum: Networking &amp; Wireless
---

### Post by Dreamer Zero on 2009-04-29
i have a HP dv6000 laptop using a AR5007EG wireless card with Madwifi, when i was using Ubuntu 8.10 64bit, it worked perfectly, now i upgraded to Ubuntu 9.04 and then started having slow speeds over wireless, after some poking around i saw i was getting packet loss to my gateway (Linksys router with Tomato firmware), i have no packet loss using the wire connection.

getting 4-10% packet loss testing at different times, running about 1000 pings per test.

when i connect to a VPN i get about 50% packet loss.

when i'm at my office i get about 0.5-1% packet loss.(currently after 15000 pings i'm seeing 0.8% loss)

i've tried adjusting router settings and MTU size with no resolve/help, searched the forums a few times and i don't see anyone with the same issue. help?

from my office wifi connection:

wlan0     Link encap:Ethernet  HWaddr 00:1e:4c:4f:d9:cd  
          inet addr:10.100.1.38  Bcast:10.100.7.255  Mask:255.255.248.0
          inet6 addr: fe80::21e:4cff:fe4f:d9cd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:431051 errors:0 dropped:0 overruns:0 frame:0
          TX packets:421335 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:76128459 (76.1 MB)  TX bytes:44400546 (44.4 MB)

i don't know what other information i can provide, i'm still a Linux newbie.

thank you.

---

### Post by Dreamer Zero on 2009-04-29
2000 ping to my home router with 6.7% loss.

wlan0     Link encap:Ethernet  HWaddr 00:1e:4c:4f:d9:cd  
          inet addr:10.21.1.6  Bcast:10.21.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:4cff:fe4f:d9cd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:41173 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56896 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17209441 (17.2 MB)  TX bytes:37845822 (37.8 MB)

no ideas?

---

