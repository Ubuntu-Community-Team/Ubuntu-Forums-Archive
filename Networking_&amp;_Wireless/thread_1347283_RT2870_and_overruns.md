---
title: "RT2870 and overruns?"
date: 2009-12-06
forum: Networking &amp; Wireless
---

### Post by garthaq on 2009-12-06
**system**
Ubuntu 9.10 - minimal install for xbmc
AsRock ION 330 System (Dual Core Atom Processor, Nvidia ION chipset, 2gb ram)
Encore Enuwi-n usb wireless-n adapter (rt2870 chipset) - using the 2.2.0.0 drivers from the ralink website with the patch to allow them to compile under ubuntu 9.10.  They are compiled for wpa_supplicant and using wpa2psk.
 
**Problem**
I have noticed severe lag with my ssh connection, and watching dvds via xbmc it has random pauses, this does not happen with a wired connection.
 
Using ifconfig I have found a significant number of overruns.
 
ra0       Link encap:Ethernet  HWaddr 00:08:54:8c:c6:64
          inet addr:10.1.1.111  Bcast:10.1.1.255  Mask:255.255.255.0
          inet6 addr: 2002:4ca7:b0d4:1234:208:54ff:fe8c:c664/64 Scope:Global
          inet6 addr: fe80::208:54ff:fe8c:c664/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4697505 errors:0 dropped:0 overruns:435 frame:435
          TX packets:2379424 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2511241751 (2.5 GB)  TX bytes:238519895 (238.5 MB)
 
This is actually a snapshot after using it for a couple hours.  The longer I try the worse it gets, I've seen it at over 10k overruns.
 
I have been looking but have yet to find anything meaningful about overruns or what to do to fix this.  All I have found is that it means the kernel is getting data faster than it can be processed, however if the processor was not able to keep up wouldn't this problem show up with the wired connection too?
 
Thanks for any help anyone can provide on this!

---

### Post by Love2MeetU on 2009-12-08
I'm having problems with an rt2870 too. Lots of people aren't even able to get it to work. Might be the problem is related.
[http://ubuntuforums.org/showthread.php?t=1342593](http://ubuntuforums.org/showthread.php?t=1342593)

---

