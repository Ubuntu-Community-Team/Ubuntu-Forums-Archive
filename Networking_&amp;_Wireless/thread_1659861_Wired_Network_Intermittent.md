---
title: "Wired Network Intermittent"
date: 2011-01-04
forum: Networking &amp; Wireless
---

### Post by RevTap on 2011-01-04
I just installed 10.10 (2.6.35-24-generic) and my wired network connection is cutting out.  I'm dual booting with Windows 7, and it works fine over there.  I'm confident it's not a hardware issue.

It works initially, but after a few minutes (this varies) the connection will drop out.  If I'm on Firefox, I'll get "Loading" until the connection times out.  If I'm using RDP to a local computer, I'll lose the connection.  When it happens, if I ping a local computer, I'll get:

64 bytes from.... icmp_req=1 ttl=128 time=4.04 ms
[long pause]
64 bytes from.... icmp_req=48 ttl=128 time=0.136 ms
64 bytes from.... icmp_req=49 ttl=128 time=0.125 ms

So I'm getting a bunch of packet loss.  Some of the time, once the packets do start going through again, Firefox will finish loading the page.  Other times, I have to click on network manager and click on "Auto eth0" which will give me the "connection established" message, and kick the network card back into gear.  Sometimes I have to do this several times.  It never shows as disconnected, but this somehow gets it going again.  Any insight would be appreciated.

lspci | grep Ethernet
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787 Gigabit Ethernet PCI Express (rev 02)

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:c9:2f:bd:9f  
          inet addr:192.168.4.119  Bcast:192.168.4.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:c9ff:fe2f:bd9f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:76359 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32738 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:45056519 (45.0 MB)  TX bytes:4236186 (4.2 MB)
          Interrupt:16

---

### Post by hebetude on 2011-01-06
I have the same problem.  Also, when I go to Wireless it works great.  It's happening a lot 10% outage per day here at work.

---

