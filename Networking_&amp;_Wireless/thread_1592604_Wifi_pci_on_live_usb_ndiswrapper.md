---
title: "Wifi pci on live usb ndiswrapper"
date: 2010-10-10
forum: Networking &amp; Wireless
---

### Post by timbalisto on 2010-10-10
I currently have 8.10 installed and my wireless card works fine. I didn't install 9.04 because of an intel graphics problem, versions beyond that fixed that problem but I could never get wireless to work. I installed 10.10 to a usb flash drive and tried it in live mode. Everything works fine except my wireless card, it doesn't even show up in proprietary hardware drivers. I installed ndiswrapper common and utils on the flash drive and tried to install the .inf file, but it still doesn't work. I want to get wifi working on the live usb before installing to my computer. I have the correct .inf and .sys files. It's a wireless-G PCI Adapter Model No. WMP54GS
Here is the lspci for my card:
```
06:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

```
Any help would be appreciated.

---

### Post by timbalisto on 2010-10-13
Bump

---

### Post by MooPi on 2010-10-13
There are a couple of posts on this issue already. Check these out.
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1595282]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1595282")
[http://ubuntuforums.org/showthread.php?t=1390174]("http://ubuntuforums.org/showthread.php?t=1390174")
Looks as if maybe a newer version of Ubuntu may also help ?

---

### Post by timbalisto on 2010-10-13
A newer version wouldn't help, I'm trying to get the network card working on the newest - 10.10. I've been all over the forums looking for a solution, I've followed several tutorials, but nothing has worked. Could it be because I'm trying to make it work on live usb?

---

