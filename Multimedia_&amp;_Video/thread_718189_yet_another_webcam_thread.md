---
title: "yet another webcam thread"
date: 2008-03-07
forum: Multimedia &amp; Video
---

### Post by PCZahra on 2008-03-07
someone mentioned the D-Link DSB-C110 worked. I have one. there is no /dev/video0 and the device manager doesn't recognise it. any ideas? (U7.10)

---

### Post by linuxwizard on 2008-03-07
Try another USB port. Post results of the command > lsusb

---

### Post by Dogalot on 2008-03-09
> **PCZahra said:**
> someone mentioned the D-Link DSB-C110 worked. I have one. there is no /dev/video0 and the device manager doesn't recognise it. any ideas? (U7.10)

I just plugged my in -- and this was the lsusb output...

robin3@dog-laptop:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 0c45:600d Microdia 
Bus 001 Device 004: ID 1267:0103 Logic3 / SpectraVideo plc 
Bus 001 Device 003: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 001 Device 002: ID 03eb:0902 Atmel Corp. 
Bus 001 Device 001: ID 0000:0000  
robin3@dog-laptop:~$ 

David

---

### Post by linuxwizard on 2008-03-09
This is where to get drivers for Microdia webcam  >> [http://www.linux-projects.org/modules/news/](http://www.linux-projects.org/modules/news/)

---

### Post by PCZahra on 2008-03-23
zahra@zahra-desktop:~$ lsusb
Bus 001 Device 004: ID 04b8:0818 Seiko Epson Corp. 
**Bus 001 Device 003: ID 06a5:d800 Divio Chicony TwinkleCam**
Bus 001 Device 002: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 001 Device 001: ID 0000:0000 

??? must be a different chipset somehow.

---

### Post by linuxwizard on 2008-03-23
PCZahra
Can't find much on your cam. But according to this > [http://translate.google.com/translate?hl=en&sl=de&u=http://forum.ubuntuusers.de/topic/77175/next/&sa=X&oi=translate&resnum=9&ct=result&prev=/search%3Fq%3DBus%2B001%2BDevice%2B003:%2BID%2B06a5:d800%2BDivio%2BChicony%2BTwinkleCam%26hl%3Den%26client%3Dfirefox-a%26rls%3Dcom.ubuntu:en-US:official%26hs%3D0PG](http://translate.google.com/translate?hl=en&sl=de&u=http://forum.ubuntuusers.de/topic/77175/next/&sa=X&oi=translate&resnum=9&ct=result&prev=/search%3Fq%3DBus%2B001%2BDevice%2B003:%2BID%2B06a5:d800%2BDivio%2BChicony%2BTwinkleCam%26hl%3Den%26client%3Dfirefox-a%26rls%3Dcom.ubuntu:en-US:official%26hs%3D0PG)
 > you need this driver > [http://www.linux-projects.org/modules/mydownloads/viewcat.php?cid=2](http://www.linux-projects.org/modules/mydownloads/viewcat.php?cid=2).

---

### Post by PCZahra on 2008-03-24
umm... so I execute the makefile?

---

### Post by PCZahra on 2008-03-30
ok, did that, installed it, ran modprobe sn9c102 and got this:
> [11455.668000] sn9c102: V4L2 driver for SN9C1xx PC Camera Controllers v1:1.48
[11455.672000] usbcore: registered new interface driver sn9c102
I don't see where that says it was unsuccessful, but according to the text file the camera should be recognised now but isn't. it's still 'unknown' and I still have no video0

---

### Post by linuxwizard on 2008-03-30
What app. are you using to test your cam with ? Camorama does not support v4l2.

---

### Post by vivalant on 2008-03-30
> **PCZahra said:**
> ok, did that, installed it, ran modprobe sn9c102 and got this:

I don't see where that says it was unsuccessful, but according to the text file the camera should be recognised now but isn't. it's still 'unknown' and I still have no video0

PCZahra, note that you are using the open version of the driver, which is less featured and only works with V4L2 applications. I suggest that you install the closed version SN9CXXX instead, which is provided as a .deb package and works with every applications. I have no problems here so far:
see http;//www.linux-projects.org

---

### Post by PCZahra on 2008-04-02
> **linuxwizard said:**
> What app. are you using to test your cam with ? Camorama does not support v4l2.

I'm testing it with the multimedia selector under system preferences. That has v4l2 in there but the camera isn't showing in dev.

> **vivalant said:**
> note that you are using the open version of the driver, .... I suggest that you install the closed version SN9CXXX instead, ...

hmm. I hesitate to try that. It says the trial version is time limited, and the paid version will only work on one kernel? I've seen several kernel updates since installing Ubuntu, I don't want to end up effectively renting my own camera.

---

