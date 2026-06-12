---
title: "Wireless Command Line Install"
date: 2010-06-13
forum: Networking &amp; Wireless
---

### Post by SOG420 on 2010-06-13
I was wondering if it was possible to do a wireless command line install? Beyond the basic install what packages would I need and what are my options for getting them? If its not possible, Can I tether my ubuntu machine with an Ethernet cable to my Win 7 machine and use its connection?
Thanks for any help

---

### Post by chili555 on 2010-06-13
Command line only? I love the way you think! 

Your options depend on the card you have. Drivers may be installed already for your card and, if so, your card may work with no further intervention. 

Drivers may be installed but you may need firmware. Or, drivers may not be installed and you may need to get them and transfer them to your computer with a USB key or CD or similar.

Let's see what you have. If you have a PCI card, run:```
lspci -nn
```Post the part that relates to your wireless and we'll have a better idea of how to proceed.

If it's USB, do the same, but with:```
lsusb
```Also, post:```
iwconfig
```Thanks.

---

