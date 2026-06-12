---
title: "02 3g modem"
date: 2009-11-10
forum: Networking &amp; Wireless
---

### Post by gcday on 2009-11-10
I have a contract o2 modem (Ovation mc930d) - has this been made to work with 9.10 and if so - how?


I was told that with 9.10, it would work out of the box but nothing happens.

---

### Post by pdc on 2009-11-11
it worked in 9.04;

[http://ubuntuforums.org/showthread.php?t=942579](http://ubuntuforums.org/showthread.php?t=942579)

these modems are called zeroCD devices: they contain windowz software and "flip" from being seen as a CD-ROM to being a USB modem:

so the technique above "flips" the way the device is seen by a virtual "eject" of the modem, that "reveals" the modem to linux

see if it works in 9.10 for you

on this post

[http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html](http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html)

if you go down to 

> Create a mobile broadband connection

does this help you configure network manager?

this link

[https://wiki.ubuntu.com/NetworkManager/Hardware/3G](https://wiki.ubuntu.com/NetworkManager/Hardware/3G)

also seems to confirm that the "eject" command will suffice; scroll down to find your device

seems the command is likely to be something like 

> sudo eject /dev/sr*           where * is whatever the device is recognised as

---

