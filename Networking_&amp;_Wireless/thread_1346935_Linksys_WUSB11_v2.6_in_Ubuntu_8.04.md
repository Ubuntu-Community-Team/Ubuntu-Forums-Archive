---
title: "Linksys WUSB11 v2.6 in Ubuntu 8.04"
date: 2009-12-05
forum: Networking &amp; Wireless
---

### Post by chris1379 on 2009-12-05
I've been trying for several weeks now to get a Linksys WUSB11 v2.6 wireless adapter to work with Hardy. According to [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#USB](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#USB)
this unit works out of the box with 9.04 but it didn't for me in 8.04. I tried ndiswrapper and it locked up the system. I also tried the driver at [http://developer.berlios.de/projects/at76c503a/](http://developer.berlios.de/projects/at76c503a/)
I see wireless networks and have connected to them for a few seconds but eventually it quits working and the Link light flashes rapidly. Can someone help me get this thing working?

Chris

---

### Post by chris1379 on 2009-12-12
I've tried everything I can find on the net and probably screwed up my Ubuntu install in so many ways. I'm thinking of installing 9.04 since this unit is reported to work with it. I have a Sony PCG-F560 with a PIII 700 and 256MB RAM. How much difference will I see in speed between 8.04 and 9.04?
 
Chris

---

### Post by chris1379 on 2009-12-13
I got it to work but I'm not sure how and it still doesn't load at boot. I followed the thread at [http://ubuntuforums.org/showthread.php?t=844275&highlight=at76](http://ubuntuforums.org/showthread.php?t=844275&highlight=at76) and copied the files to /lib/modules/2.6.24-26-generic/ubuntu/wireless/at76. Now it seems that the file at76_usb.ko was installed also in /lib/modules/2.6.24-26-generic/kernel/drivers/net/wireless by "make install" but the other files 
at76_usb.c
at76_usb.h
at76_usb.mod.c
at76_usb.mod.o
at76_usb.o
at76_usb.spec
compat.h
Module.symvers
are not there. If I just run "sudo modprobe at76_usb" from the command line, the unit becomes active but won't connect to anything. Instead I have to run "sudo modprobe at76_usb" from /lib/modules/2.6.24-26-generic/ubuntu/wireless/at76. Then it works normally. So what do I have to do to get this thing properly installed and working at boot?

---

