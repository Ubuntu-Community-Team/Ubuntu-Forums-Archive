---
title: "my usb 3g modem does not seems to be working"
date: 2010-11-07
forum: Networking &amp; Wireless
---

### Post by hero1900 on 2010-11-07
when i plug the modem i can access to its software installation for windows. but i cant connect using it
i read in the ubuntu documentation some stuff on how to add a module to the kernel
so i did lsusb to see my device and i found that the modem is defined as [SIZE=2]Bus 002 Device 007: ID 05c6:f000 Qualcomm, Inc. 
so i did use [/SIZE]
sudo modprobe usbserial vendor=0x[SIZE=2]05c6[/SIZE] product=0x[SIZE=2]f000

[SIZE=3][FONT=Arial]to load this module to the kernel 
and as the documentation says i should found in /dev/  ttyUSB0 or ttyACM0
but i cant see any of them i dont know what to do now any suggestions?

[/FONT][/SIZE][/SIZE]

---

### Post by ieee488 on 2010-11-07
Try 10.10
With every revision, the support for mobile broadband gets better and better.

---

### Post by hero1900 on 2010-11-07
that desktop cant have 10.10 since it will give me black screen and cant install ubuntu

---

### Post by bouncingwilf on 2010-11-07
If you can see the software to install then it's probably being detected as a CD device ( mine did when I set it up only yesterday).

The trick is to either find the device under nautilus and "eject" what it believes to be the CD ( or an icon may appear on the desktop; rt-click;eject)  and then you should be able to initiate a connection with the network manager applet in the tool bar. - Worked for me


Bouncingwilf

---

### Post by dineshs on 2010-11-08
Have you seen this
[http://ubuntuforums.org/showthread.php?t=1371806](http://ubuntuforums.org/showthread.php?t=1371806)
Here is a guide by alexfish
[http://ubuntuforums.org/showthread.php?t=1466490](http://ubuntuforums.org/showthread.php?t=1466490)

---

### Post by halj32 on 2010-11-08
the easiest way to get a 3G dongle working is to install
"usb-modeswitch" 
good luck

---

