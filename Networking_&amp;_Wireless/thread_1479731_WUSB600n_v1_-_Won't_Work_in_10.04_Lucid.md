---
title: "WUSB600n v1 - Won't Work in 10.04 Lucid"
date: 2010-05-11
forum: Networking &amp; Wireless
---

### Post by Dev0 on 2010-05-11
I've read many threads about the Linksys WUSB600n (both versions), and tried the suggested solutions to no avail in 32-bit Ubuntu 10.04.  Compiling my own drivers, adding items to the blacklist, and even a clumsy driver transplant  from 32-bit 9.10 have all failed.

So here's the sitch:
I have a Linksys WUSB600n v1 that works perfectly in 9.10 with only the minor modification posted by chili555 in this thread [HTML]http://ubuntuforums.org/showthread.php?t=1423100[/HTML]

That solution was:
"
```
sudo gedit /etc/modprobe.d/blacklist.conf
```
Add three lines:```
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib
```"
I've tried the same in a clean install of 10.04, but no connection is made and a prompt comes up every few minutes asking for the password. I've used the included rt2870 driver in 9.10 without problems.  My wireless-N network uses WPA2 personal encryption, which has never given me issues.

The usb id of my adapter, per lsusb, is ID 1737:0071
I used ```
lsmod | grep -e rt2 -e rt3
```to see what drivers load in both versions of Ubuntu.  The results are:
for 9.10: rt2870sta             488820  1 
for 10.04: rt2870sta             461811  1 

Ideas?

---

### Post by lisati on 2010-05-18
Thread closed at the request of the OP

---

