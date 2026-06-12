---
title: "Ubuntu 8.10 networking problem"
date: 2009-02-16
forum: Networking &amp; Wireless
---

### Post by OOzypal on 2009-02-16
Hello,

I have dual OS installed Ubuntu and XP. I am having a problem with networking in Ubuntu. Sometime when I start ubuntu I can not browse the net nor I can ping my router and sometime it happens after working of some time.

When I start the PC and go to XP the net and pinging works ok. 

At first, I though the problem from the LAN (5 computers connected through router with Win2003 server) so I switched to another point/connection in the wall and the problem still exists.

This problem is intermittent and it is not a hard fault.

I am writing this post from XP. I will now switch to Ubuntu and see.

---

### Post by OOzypal on 2009-02-16
Hello

I am now running Ubuntu and net and pinging work ok. Here is the outcome of the ping

```
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=255 time=0.613 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=255 time=0.609 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=255 time=0.580 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=255 time=0.619 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=255 time=0.609 ms
64 bytes from 192.168.1.1: icmp_seq=6 ttl=255 time=0.587 ms
64 bytes from 192.168.1.1: icmp_seq=7 ttl=255 time=0.584 ms
64 bytes from 192.168.1.1: icmp_seq=8 ttl=255 time=0.597 ms
64 bytes from 192.168.1.1: icmp_seq=9 ttl=255 time=0.609 ms
64 bytes from 192.168.1.1: icmp_seq=10 ttl=255 time=0.609 ms
64 bytes from 192.168.1.1: icmp_seq=11 ttl=255 time=0.636 ms
64 bytes from 192.168.1.1: icmp_seq=12 ttl=255 time=0.622 ms

--- 192.168.1.1 ping statistics ---
12 packets transmitted, 12 received, 0% packet loss, time 11000ms
rtt min/avg/max/mdev = 0.580/0.606/0.636/0.021 ms
```

---

### Post by zander1013 on 2009-02-16
i don't know what your isp arangements are but mine limits the number of computers connected to four. and if you connect more then four it starts cutting out.

---

### Post by OOzypal on 2009-02-16
There is no limit for my ISP. Even though the ISP cuts it off, I should be able to ping my router right!

---

### Post by zander1013 on 2009-02-16
> **OOzypal said:**
> There is no limit for my ISP. Even though the ISP cuts it off, I should be able to ping my router right!

it looks like you are reaching your router if that is what the ping output is from.

---

