---
title: "Medialink Mwn-usb150n; HP pavilion laptop"
date: 2012-08-04
forum: Networking &amp; Wireless
---

### Post by StrobeWylan on 2012-08-04
I just put Ubuntu 10.04 on a friend's HP pavilion "Entertainment" laptop. everything works fine, hooked up to my Ethernet. 
He has a wireless hookup in his place. I'm trying to get his Medialink Mwn-usb150n to work. 

I downloaded the driver. Right clicked on it and used archive manager to extract the file to his home folder.
Opened a terminal and pasted the following into the terminal:

cd ~/2009_0525_RT3070_Linux_STA_v2.1.1.0 (hit enter)

make (hit enter)

After running got the message "[Linux] error 2"

Opened a terminal and entered: lsusb

Result:
laptop:~$ lsusb 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 001 Device 002: ID 148f:3070 Ralink Technology, Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 

Thanx to anyone who can help. (Please keep it simple)

---

