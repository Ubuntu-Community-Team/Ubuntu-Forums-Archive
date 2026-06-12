---
title: "Jaunty Broadcom 4328 rev 03: device not managed"
date: 2009-07-22
forum: Networking &amp; Wireless
---

### Post by lduperval on 2009-07-22
Hi,

I updated my system from hardy -> intrepid -> Jaunty and everything works, so far, except the wireless. I have this card:

04:00.0 Network controller [0280]: Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 03)

I tried what is explained here:

[http://ubuntuforums.org/showthread.php?t=1134564](http://ubuntuforums.org/showthread.php?t=1134564)

I tried restarting the NetworkManager applet but to no avail. When I try to connect, it says "device not managed".

iwconfig says:

[http://ubuntuforums.org/showthread.php?t=1134564](http://ubuntuforums.org/showthread.php?t=1134564)

ifconfig says:

wlan0     Link encap:Ethernet  HWaddr 00:1a:73:91:66:6f  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:73ff:fe91:666f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:2 dropped:0 overruns:0 frame:265900
          TX packets:37 errors:14 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:4327 (4.3 KB)
          Interrupt:21 

I am unsure where the problem lies. Any ideas? I am on an AMD64 system.

Thanks,

L

---

### Post by superprash2003 on 2009-07-22
take a look at this [http://www.prash-babu.com/2009/05/how-to-fix-ubuntu-network-manager-error.html](http://www.prash-babu.com/2009/05/how-to-fix-ubuntu-network-manager-error.html)

---

### Post by lduperval on 2009-07-22
Works great! Thanks!

L

---

