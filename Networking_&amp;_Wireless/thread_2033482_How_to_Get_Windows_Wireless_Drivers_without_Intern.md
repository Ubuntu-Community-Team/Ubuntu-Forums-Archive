---
title: "How to Get Windows Wireless Drivers without Internet?"
date: 2012-07-26
forum: Networking &amp; Wireless
---

### Post by mmandemlin on 2012-07-26
Hello! :D

I just started on this forum a literally few minutes ago and I am absolutely brand new to Ubuntu it's self so I know practically nothing about it, but I am a long time Windows user. I have a Netgear WNDA3100v2 (chipset: Broadcom BCM43XX) wireless adapter, I am using my friends copy of Ubuntu 11.10 and I have noted the lack of a functioning Netgear WNDA3100v2 drivers. I already have the drivers from the internet. But... I need the Windows Wireless Drivers, and the computer that I need it for isn't connected to the internet. We do have a router but all of the plugs are in use. And I need that computer connection to the internet so we can make our home e-mail server.

Please Help! :(

Thank You! :KS

---

### Post by threedaysmore on 2012-07-26
What exactly are you looking for when you say that you "need the Windows Wireless Drivers"?  What do you need them for? Just try to to be specific about what exactly your set up is and what problems you're encountering.

Cheers mate.

---

### Post by chili555 on 2012-07-26
You can easily download them on any other computer on the network and transfer them with a USB key or similar. > Netgear WNDA3100v2 (chipset: Broadcom BCM43XX)This has been covered and solved a few times on the forum. Please plug in your device and find out the usb.id with the terminal command:```
lsusb
```It will be something like, but not exactly, 0846:9020.

Search for your ID on the forum, look for the magic words SOLVED and several posts have the files attached. If you can't find any, post your usb.id and I probably have them.

---

