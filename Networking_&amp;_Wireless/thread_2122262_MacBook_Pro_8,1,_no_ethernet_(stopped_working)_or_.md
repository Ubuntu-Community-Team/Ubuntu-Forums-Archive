---
title: "MacBook Pro 8,1, no ethernet (stopped working) or wifi (never worked)"
date: 2013-03-04
forum: Networking &amp; Wireless
---

### Post by rafaltrus on 2013-03-04
I know this is an issue affecting many people, but I could not resolve mine even following instructions from other threads.

It might be irrelevant information, but I installed Ubuntu on my Macbook Pro alongside Mac OS. I had ethernet connection (with Live CD and after I installed Ubuntu 12.10). Then I decided I want Windows as well. I installed Windows, I had to reinstall Ubuntu (rEFIt wouldn't recognise the Ubuntu installation), and after that I could no longer connect via Ethernet; neither from Live CD, nor from the installed Ubuntu system. I cannot think of a reason why it would stop detecting my Ethernet device (it works on Windows and Mac OS).

Here is the output for 'sudo ifconfig':

> 
eth0 Link encap:Ethernet HWaddr c8:2a:14:4a:ed:16 
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:16 

lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:112 errors:0 dropped:0 overruns:0 frame:0
TX packets:112 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:9056 (9.0 KB) TX bytes:9056 (9.0 KB) 


Any ideas how to fix my Ethernet and WiFi (since I'm already here)? What other information would you need to help me figure it out?
Thanks!

---

