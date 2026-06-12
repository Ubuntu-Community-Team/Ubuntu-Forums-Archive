---
title: "Netgear MA101 USB Wireless Adapter Rev. A"
date: 2006-02-24
forum: Networking &amp; Wireless
---

### Post by diplomo on 2006-02-24
Hey all, I'm new to the forum, but I'd like to get involved so here I am. I've been using the Breezy live CD to test hardware compatibility and I was ready to install ndiswrapper and the atmel drivers after reading about linux compatibility for the netgear MA101 but turns out its was automatically detected by breezy and all I had to do was put in the SSID and Network key and it worked straight away. What I was wondering is if this has anything to do with the presence of the Windows OS on the machine and will it still be detected on a Ubuntu (installed) system?

---

### Post by az on 2006-02-24
[QUOTE=diplomo]What I was wondering is if this has anything to do with the presence of the Windows OS on the machine and will it still be detected on a Ubuntu (installed) system?[/QUOTE]
No.  Quite a few wireless cards have native linux drivers.  Actually, only a few wireless cards require that you use ndiswrapper.  Most have working linux drivers and function right out of the box.

Ndiswrapper is pretty dumb - just like any other computer application.  You really have to specify the windows driver for it to use.  It cannot guess on it's own.

Your windows partition if probably not even mounted anyway...

---

### Post by diplomo on 2006-02-24
Thanks for the reply. I was just wondering, Netgear doesn't actually offer Linux drivers for the device...its also one of those external USB adapters, its not a wireless card, anyway, who am I to complain if it works, just thought I'd let others now that it is compatible. Go Breezy for making life easy for me....

---

### Post by az on 2006-02-24
[QUOTE=diplomo]Thanks for the reply. I was just wondering, Netgear doesn't actually offer Linux drivers for the device...its also one of those external USB adapters, its not a wireless card, anyway, who am I to complain if it works, just thought I'd let others now that it is compatible. Go Breezy for making life easy for me....[/QUOTE]

Whether it is pci, usb pcmcia, it doesn't matter.  It's a wireless device.

And a lot of the hardware that is supported in linux is done so without the manufacturer's (or vendor's) cooperation....  Ain't it great?

---

