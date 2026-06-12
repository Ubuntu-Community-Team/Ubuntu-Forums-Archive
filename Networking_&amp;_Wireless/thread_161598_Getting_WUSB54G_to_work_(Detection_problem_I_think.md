---
title: "Getting WUSB54G to work (Detection problem I think)"
date: 2006-04-17
forum: Networking &amp; Wireless
---

### Post by Squirell on 2006-04-17
Alright, first thing is this is my first time using linux so I don't quite know what I'm doing yet. I have a Linksys WUSB54G wireless card that I'm trying to get working with Ubuntu. I have the default Ubuntu install.

When I go to System->Admin->Networking I only get the ethernet and modem adaptors. Obviously neither of these do me much good. 

The device manager shows the wireless card, but all the properties are unknown, and lsusb gave me 131b:000d as the device id.

So I tried installing the drivers
-sudo ndiswrapper -i whatever.inf
*Driver installed message*
-sudo ndiswrapper -d 131b:000d whatever.inf
*Sucess message*
-sudo ndiswrapper -m
*alias wlan0 whatever stuff*
-sudo iwconfig
*No wireless extensions*

So I rebooted and this is the current state
(In the terminal. Its not a direct copy becuase I don't have internet on that computer, sorry)
-sudo ndiswrapper -l
Installed ndis drivers:
rt2500usb driver present, hardware present
-sudo iwconfig
lo        no wireless extensions
eth0    no wireless extensions
sit0     no wireless extensions

So what am I doing wrong?/What do I need to do?

By the way, the machine is dual-booted with windows, and under windows the card works if that makes a difference.

---

### Post by jml on 2006-04-17
Here is a link on Ubuntu's Wiki covering all manner of wireless configuration issues.  There will probably be something in here to help you.

[https://wiki.ubuntu.com/WifiDocs](https://wiki.ubuntu.com/WifiDocs)

Good luck.

Joe

---

### Post by Doctor Moley on 2006-05-05
Did you ever figure this out? I've got exactly the same problem right now.

---

### Post by Doctor Moley on 2006-05-05
Actually I just got it to work! Just had to add ndiswrapper to /etc/modules file and rebooted. It freezes on boot loading modules if the dongle is plugged in, but it works fine otherwise.

---

