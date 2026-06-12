---
title: "Solution: Zonet ZEW2500P w/ ndiswrapper"
date: 2006-06-27
forum: Networking &amp; Wireless
---

### Post by parksobong on 2006-06-27
I've been struggling with getting my zonet wireless usb device to work with Linux.

But for those who are having the same problem (after cross-referencing a few threads on this awesome forum), here is what I did to get it up and running.

First of all, Dapper Drake auto-detects the ZEW2500P, but it did not work for me. It froze my laptop when I opened up System > Administration > Networking

So I blacklisted rt2570 on the file /etc/modprobe.d/blacklist

Then using Synaptic, I downloaded ndiswrapper-utils

After, in the console:

sudo ndiswrapper -i (location of rt2500.inf WinXP driver on Zonet OEM CD)

I then added ndiswrapper to /etc/modules, so that the module would boot up with ubuntu

Finally, after rebooting, I accessed System > Administration > Networking and configured the wlan0 card and then activated it.

Reboot again, and you are connected.

---

