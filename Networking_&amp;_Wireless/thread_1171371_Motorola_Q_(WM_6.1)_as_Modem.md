---
title: "Motorola Q (WM 6.1) as Modem"
date: 2009-05-27
forum: Networking &amp; Wireless
---

### Post by amj on 2009-05-27
Hi, 

I'm trying to get a Motorola Q9H (european version), running WM 6.1 to act as a modem with my laptop running Ubuntu 9.04. 

I've been reading through the forums, and have been going through a lot of the suggestions.  I feel I'm close, but I'm just not quite there. 

I am connecting via the USB port, and I have the USB set to "ActiveSync Rndis".  As such, phone appears as a wired network connection, eth1.  ipconfig eth1 gives the following info:

```

eth1      Link encap:Ethernet  HWaddr 80:00:8d:3f:32:43  
          inet addr:169.254.2.125  Bcast:169.254.2.127  Mask:255.255.255.252
          inet6 addr: fe80::8200:8dff:fe3f:3243/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26 errors:89 dropped:0 overruns:0 frame:1
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2680 (2.6 KB)  TX bytes:9566 (9.5 KB)

```

This is in contrast to [_this post_]("http://http://ubuntuforums.org/showthread.php?t=1025877&highlight=wm6.1+modem"), which shows a more valid IP address of 192.168.0.102

If, at this point, I try to connect Internet Connection Sharing on the phone, I get an error message stating "Check USB Cable Connection".

If, on the other hand, I set the USB port to "modem" and try to get a "Mobile Broadband" connection, nothing happens.  But if I move my SIM to another Motorola phone (V1100), and set it's USB connection to modem, I can connect the modem as a "Mobile Broadband" connection, with ease. 

Any pointers for the next step?  I'm a bit baffled. 

Cheers, 
AJ

---

