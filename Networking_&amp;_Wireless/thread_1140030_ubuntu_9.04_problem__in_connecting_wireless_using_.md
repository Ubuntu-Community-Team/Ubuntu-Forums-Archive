---
title: "ubuntu 9.04 problem  in connecting wireless using wvdial"
date: 2009-04-27
forum: Networking &amp; Wireless
---

### Post by linuxisfantastic on 2009-04-27
I just upgraded to 9.04 version of Ubuntu using broadband internet. I have used my reliance wireless internet before in Ubuntu 8.10, and it worked well when I use wvdial. But after upgrading to 9.04, whenever I execute the following command:-

sudo modprobe usbserial vendor=0x19d2 product=0xfffd

It says "FATAL: Module usbserial not found."

If I execute just "sudo wvdial" it says it cannot locat the file "/dev/ttyUSB0"


What should I do??? Can anyone help? I am 100% sure it is because of the upgrade, because it did work well in ubuntu 8.10

Also, my modems working well, because I have XP windows with me, and it works in that OS.


[CENTER]:confused:
[/CENTER]

---

### Post by rudied on 2009-04-28
Please try the following options 
<https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345002>

---

