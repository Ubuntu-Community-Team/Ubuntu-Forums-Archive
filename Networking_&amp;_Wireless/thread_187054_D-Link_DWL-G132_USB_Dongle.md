---
title: "D-Link DWL-G132 USB Dongle"
date: 2006-06-02
forum: Networking &amp; Wireless
---

### Post by RalphS on 2006-06-02
I have one of these with Ubuntu 6.06 (fresh install), its not working, only appears on the device manager as a use wireless device, nowhere else. 

The D-link website has a list of hardware that has linux drivers available, buts it not on there. I have no idea what chipset its based on.

Anyone know if I am going to have any luck with this, or even anywhere to begin?

---

### Post by skyshark88 on 2006-06-03
i got my usb dongle working using usb package from repository and configure network card module from add/remove section.

zd1211 wireless driver module

---

### Post by skyshark88 on 2006-06-03
Ohh, by the way do not boot up with usb dongle attached, plug in after you sign in............

---

### Post by lynxus on 2006-06-03
Try the following thread :)
It may help as its worked for other wifi cards/dongles

[http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

---

### Post by RalphS on 2006-06-05
I think I have it working using ndiswrapper and the drivers from the D-Link site, it appears in the network manager. It lists the availabe access points, but I have not get figured out how to get WPA-PSK configured so I can connect (the GUI only appears to support wep).

Cheers.

---

### Post by totoprout on 2006-09-04
I've just buy this dongle too ...
In a first time, ndiswrapper (with official windows d-link driver loaded) seems to work well. But sometimes, when I plug/unplug it, my desktop freeze ... and I'm not alone : [http://ubuntuforums.org/showthread.php?t=240350&highlight=dwl-g132](http://ubuntuforums.org/showthread.php?t=240350&highlight=dwl-g132)

---

