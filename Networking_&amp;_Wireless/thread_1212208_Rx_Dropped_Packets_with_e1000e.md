---
title: "Rx Dropped Packets with e1000e"
date: 2009-07-13
forum: Networking &amp; Wireless
---

### Post by MattFS218 on 2009-07-13
I use my server for some pretty intensive VoIP media processing typically pushing about 200Mbps/sec throughout the day.

Today, I noticed on one of my servers is producing a high number of Rx dropped (packets) as reported by ifconfig. I tried disabling ipv6, but the problem still persists. 

What other things can I try to remedy the problem? Could it be related to the upstream switch?

Thanks.

--matt
[http://www.hellohunter.com](http://www.hellohunter.com)

[    2.254037] e1000e: Intel(R) PRO/1000 Network Driver - 0.3.3.3-k6
[    2.254039] e1000e: Copyright (c) 1999-2008 Intel Corporation.
[    2.254072] e1000e 0000:00:19.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.254078] e1000e 0000:00:19.0: setting latency timer to 64

root@vcserver4:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:30:48:b0:6f:57
          inet addr:64.XXX.XX.XX  Bcast:64.XXX.XX.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:50098182 errors:0 dropped:169641 overruns:0 frame:0
          TX packets:15375281 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:8990079463 (8.9 GB)  TX bytes:3299286772 (3.2 GB)
          Memory:df300000-df320000

---

### Post by jonobr on 2009-07-14
If I was seeing a lot of packets dropped, I would be considering things like maybe MTU sizes , drivers in use, cabling issues, faulty hardware you may be using , autonegotation not working correctly etc, Hopefully you have a similar instance where you can compare between installations.

It the drivers and systems are the same , which I would reckon they would be,
then I would swap ports if you can, and then cables.

I think your really left with a process of elimination.

One question though, has this just happened all the sudden or do you think its be going like this for a while?

---

### Post by MattFS218 on 2009-08-18
jonobr, thanks for the reply. I finally have another box on the same switch, so I'll try playing around with different cable and port combinations. To answer your question tho, this packet loss I'm describing seeing in ifconfig has been going on ever since the machine was turned up, so it didn't occur from any sort of software change. Thanks for the help.

--matt
[hosted dialer & voice broadcasting]("http://www.hellohunter.com")

---

