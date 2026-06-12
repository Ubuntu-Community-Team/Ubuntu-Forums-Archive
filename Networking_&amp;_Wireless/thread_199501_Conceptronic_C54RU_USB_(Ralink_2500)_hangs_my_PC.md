---
title: "Conceptronic C54RU USB (Ralink 2500) hangs my PC"
date: 2006-06-18
forum: Networking &amp; Wireless
---

### Post by Alandor on 2006-06-18
Hi, i write this becausse I hope someone can helpme. I installed recently Xubuntu Desktop, and tried to use my USB wirelass card "conceptronic C54RU). It was detected great by Xubuntu, and even detected my home network one time. But the problem comes when i configure it and It tries to connect suddenly It hangs completely my PC. It only hangs when trying to connect o when creating a wlan. How can I fix this ??

 Later, looking in the console I saw this when I plug the USB card:

"new full speed USB device using uhci_hcd and address 2
 idVendor = 0x14b2, idProduct = 03c02
 INIT bRadio=1
 usbcore: registered new driver rtusb
 rausb0 (WE) : Driver using old /proc/net/wireless support, please fix driver !
 RT25usb  Driver version 1.1.0"

 I hope this can help more on fixing the problem.

 Thanx for your help. :)

P.D.: I tried then to connect my other USB wireless card (SMC model: SMC2862W-G)  and, it doesn't worked, but this time it is detected but can't be configured, it freezes all tries to use the ifconfig or iwconfig commands or the GUI...... Is there possible to use both cards from linux/ubuntu ??

---

### Post by cblanquer on 2007-02-03
Probably you solve3d already. 
If not try that one (Spanish), it helped me - remember to check with "lsusb" which is the actual chip version in order to install the proper drive.

---

### Post by mingotta on 2007-05-04
Hello, I have the same USB wireless device and am trying to make it work with Ubuntu Feisty.

I still haven't found out what chipset it's shipped with.

The reply to the initiator of this thread says we should take a look at the output of lsusb, but it tells me nothing useful:

> root@GlaucosUbuntuBox:~# lsusb
Bus 004 Device 003: ID 14b2:3c22  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  


What can I do, please, to at least install the correct driver?

---

### Post by mingotta on 2007-05-04
This page gave me a hint: [http://www.qbik.ch/usb/devices/showdev.php?id=3104](http://www.qbik.ch/usb/devices/showdev.php?id=3104)

It says > The Dongle has a build in RaLink chipset rt2570 which is supported by official driver from RaLink (see [http://www.ralinktech.com)](http://www.ralinktech.com)). A free project is working on a better driver based on the one from RaLink [http://rt2400.sf.net](http://rt2400.sf.net) Visit also rt2x00.serialmonkey.com
I'll try rt2570 then and see what happens!

---

### Post by cblanquer on 2007-05-06
The driver is either rt2570 or rt73, you can guess it depending on the lsusb data.
I could not find the informatin source and are currently not under linux so that I cannot tell you which one to choose... sorry you should try either of them. If you bought it recently use RT73 anyway.
Good luck.

---

### Post by cblanquer on 2007-05-08
Currently downloading serialmonkey drivers and trying that one: [http://ubuntuforums.org/showthread.php?t=400236&highlight=rt73](http://ubuntuforums.org/showthread.php?t=400236&highlight=rt73)

---

