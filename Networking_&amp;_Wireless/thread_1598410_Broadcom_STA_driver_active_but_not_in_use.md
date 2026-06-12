---
title: "Broadcom STA driver active but not in use"
date: 2010-10-16
forum: Networking &amp; Wireless
---

### Post by molimonster on 2010-10-16
After trying to make audio output work on Lenovo b560 notebook I finally succeeded but the wireless stopped working. The driver was removed. I tried to follow the instructions from Broadcom [http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt) and it started showing the driver in admin - drivers, it shows that it is activated but not in use, but once I get to this point 
"[I]modprobe wl"
it shows this:

[/I][I]install /sbin/modprobe --ignore-install wl 
insmod /lib/modules/2.6.32-25-generic-pae/updates/dkms/wl.ko 
FATAL: Error inserting wl  (/lib/modules/2.6.32-25-generic-pae/updates/dkms/wl.ko): Unknown symbol  in module, or unknown parameter (see dmesg)
FATAL: Error running install command for wl

I tried this as well

[/I]sudo modprobe -r b43 ssb wl sudo modprobe wl
 no improvement though.
i'm on 10.04

---

### Post by bkratz on 2010-10-16
> **molimonster said:**
> After trying to make audio output work on Lenovo b560 notebook I finally succeeded but the wireless stopped working. The driver was removed. I tried to follow the instructions from Broadcom [http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt) and it started showing the driver in admin - drivers, it shows that it is activated but not in use, but once I get to this point 
"[I]modprobe wl"
it shows this:

[/I][I]install /sbin/modprobe --ignore-install wl 
insmod /lib/modules/2.6.32-25-generic-pae/updates/dkms/wl.ko 
FATAL: Error inserting wl  (/lib/modules/2.6.32-25-generic-pae/updates/dkms/wl.ko): Unknown symbol  in module, or unknown parameter (see dmesg)
FATAL: Error running install command for wl

I tried this as well

[/I]sudo modprobe -r b43 ssb wl sudo modprobe wl
 no improvement though.
i'm on 10.04

I notice you are using the pae kernel, you probably will be interested in this bug report

[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/576502](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/576502)

---

### Post by kik on 2010-11-13
I have Lenovo B560 with specifications:
> 
Intel Dual-Core P6100 3MB Cache
500GB HDD
2GB SODIMM DDR3 1066 MHz
15.6" TFT HD [LED] 1366x768
Wi-Fi IEEE 802.11b/g/n
Integrated graphics card
DVD±RW Dual Layer
Touchpad, TrackPoint
SecureDigital Card, MultiMedia Card, MemoryStick, MemoryStick Pro
1x 15-pin D-Sub (display output), 3x USB 2.0, 1x RJ-45 (LAN), 1x E-SATA/USB Combo, 1x combo audio
1x10/100/1000BaseT Gigabitethernet (RJ45), Stereo Loudspeaker, mikrophone, Integrated camera;


I installed Ubuntu 10.10 :)

I installed Wi-Fi through System->Administration->"Additional Drivers".
In the end I have this view:
[IMG]http://albinas.lt/uploads/LenovoB560/AdditionalDrivers.png[/IMG]

And then on [IMG]http://albinas.lt/uploads/LenovoB560/wifi-bad.png[/IMG] or [IMG]http://albinas.lt/uploads/LenovoB560/wifi.png[/IMG]
I pressed right click and checked on "Enable Wireless" and after some time when I pressed on it left click it showed me wifi network access points.


Webcam also worked out of the box. I only installed **cheese** that makes photos. And if I want to take a photo I go to Applications->"Sound & Video"->"Cheese Webcam Booth" and then I can make a photo from webcam point of view.

I have problems only with sound. I don't know how to make it working.

P.S. I am from Lithuania and English is my second language :))

---

### Post by jcparker500 on 2010-11-13
I am facing the exact same problem as Kik above.  His screen shots may as well have been mine.  Lenovo G560 and no sound in Ubunto 10.10 64 bit.  Please keep in mind that I am brand new to Linux.  I don't know anything about recompiling the kernel or things of that nature.  I am actually running off of the CD to see if it has drivers for everything before I install it on my hard drive.  I really want to use Ubuntu as I love the GUI and the speed, but sound is very important to me.  Anyone know if there is a simple enough fix for this for a newbie?

---

