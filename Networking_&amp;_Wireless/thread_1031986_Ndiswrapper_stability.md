---
title: "Ndiswrapper stability"
date: 2009-01-05
forum: Networking &amp; Wireless
---

### Post by BDubs588 on 2009-01-05
Ok, so I've had ubuntu for about 3 days on a dual boot system with Windows XP.  The only thing thats preventing me from using Ubuntu most of the time is ndiswrapper.  I've had nothing but trouble with this program.  I'm using a DWL-G132 usb device and I can get it connected for about 3 minutes before I lose connection.  I can see the wireless router through the network options, but when I try to connect it just keeps asking for my network key.  When I try removing the device and re-inserting it, its like the device loses all of its power with no lights at all working and "sudo modprobe ndiswrapper" has absolutely no effect in restarting the device.  The only way to get it working again in Ubuntu is to remove it, boot to the windows login, plug it in so the lights come on, and then restart into Ubuntu again where I repeat the whole process.  I installed both drivers through ndiswrapper exactly like previous forum posts have said so I have no idea what could be wrong.  Any help would be greatly appreciated.  I haven't been able to enjoy Ubuntu fully because of this. :confused:

---

### Post by BDubs588 on 2009-01-06
Bump

---

### Post by wieman01 on 2009-01-06
Could this be a power supply issue? How many USB device have you got? An external USB power supply/hub might be a remedy. It was in my case.

---

