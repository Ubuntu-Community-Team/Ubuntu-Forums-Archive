---
title: "Can not find wireless internet, Ubuntu 10.04, Broadcom 4727"
date: 2011-05-18
forum: Networking &amp; Wireless
---

### Post by hokori616 on 2011-05-18
My Laptop, a Lenovo B560 with a Broadcom 4727, with Ubuntu 10.04 do not find any wireless network connections even though I got a router about one meter from it and even though my other computer, the laptop that I am writing from and that is running Linux Mint 8, do find about 15. 
I have found a lot of threads about this already, however I got the problem that I can not provide the computer laptop with a wired connection and hence can I not download anything, which seem to be the normal solution to this problem. Therefore am I wondering if there is any other way to make the laptop find networks. I should probably also say that I got windows drives for it on a separate harddrive and that the laptop worked fine with finding networks when windows was installed on it.
// Thanks on beforehand

---

### Post by Kaplan Crunch on 2011-05-18
Have you checked the output for 'iwconfig' and 'ifconfig' to make sure your wireless card is up and searching?


~KC

---

### Post by hokori616 on 2011-05-18
iwconfig give me
lo - no wireless extensions
eth0 - no wireless extensions
pan0 - no wireless extensions

ifconfig give me
eth0 Link encap:Ethernet HWaddr f0:de:f1:0e:5b:94
        UP BROADCAST MULTICAST MTU:1500 Metric:1
        RX packets: 0 errors:0 dropped: 0 overruns:0 frame: 0
        TX packets: 0 errors:0 dropped:0 overruns:0 carrier: 0
        collisions:0 txqueuelen: 1000
        RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
        Interrupt: 34

lo     Link encap: Local Loopback
        inet addr: 127.0.0.1   Mask:225.0.0.0
        inet6 addr: ::1/128 Scope:Host
        UP LOOPBAK RUNNING  MTU:16436 Metric:1
       RX packets: 160 errors:0 dropped:0 overruns:0 frame:0
       TX packets:160 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:0
       RX bytes:12608 (12.6 KB)  TX bytes:12608 (12.6 KB)

---

### Post by josephmills on 2011-05-18
hi there I am also working on this with someone at this thread [http://ubuntuforums.org/showthread.php?t=1743723](http://ubuntuforums.org/showthread.php?t=1743723) hope that this helps

---

### Post by hokori616 on 2011-05-18
After that I followed this link, [http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt) , that I found in josephmills link did everything work out, thank to you both.__

---

