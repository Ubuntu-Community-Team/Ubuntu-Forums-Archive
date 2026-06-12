---
title: "wireless adapter not recognied"
date: 2012-05-12
forum: Networking &amp; Wireless
---

### Post by ubu10 on 2012-05-12
I had this D-link DWA-125 USB wireless adapter working fine on my ubuntu 11 powered desktop computer. One day the system doesn't recognize the device at all, not LED glowing on the device. It, however works fine when I run Win7 on the same machine, so there is no fault with the device. I tested with all available USB ports, yet the same result. I guess there has to be some conflict issue.   I tried to troubleshoot myself, here are the results:       

> 
~$nm -tool
wired properties
carrier: off

~$ lshw -C network
description: Ethernet interface
.....
configuration: ....driver = r8169....



~$ sudo lsusb
.....
Bus 001 Device 012: ID 07d1:3c16 D-Link system DWA-125 N 150 Adapter (rev.A2) [Realink rt2870]


~$ sudo lsmod
....
r8169     52788     0
....


~$ sudo iwconfig
lo     no wireless extension
eth0   no wireless extension




Can anyone guide me on how to solve this?

---

### Post by ubu10 on 2012-05-12
Sorry moderators, I got the solution here : 

[http://kaustav.codebinders.com/2011/10/install-dwa-125-wireless-driver-on-ubuntu-11-10.html](http://kaustav.codebinders.com/2011/10/install-dwa-125-wireless-driver-on-ubuntu-11-10.html)

You may please deleted the original post.

---

