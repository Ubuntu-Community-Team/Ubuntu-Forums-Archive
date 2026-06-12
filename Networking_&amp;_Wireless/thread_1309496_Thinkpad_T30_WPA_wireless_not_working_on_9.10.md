---
title: "Thinkpad T30 WPA wireless not working on 9.10"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by The Mad Scientist on 2009-11-01
I upgraded to 9.10 from 9.04 during beta, and my wireless networking lost WPA capability, which effectively makes it worthless on my home network.  I assumed it was a beta issue, but it is still there with the release.  This issue occurred with my 8.10 to 9.04 upgrade, as well, but was fixed about a month after release with a patch.

From the info I can gather, it appears the orinico driver is being incorrectly used (orinico does not support WPA).  Blacklisting orinoco leads to a hang on boot.  Here is the current info:

IBM T30 Laptop
512MBytes RAM
Xubuntu 9.10 release (clean install)

lspci gives:
02:02.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)

lsmod shows:
orinoco_pci             4700  0 
orinoco                63600  1 orinoco_pci

Any hints on how to solve this?

---

### Post by rofthorax on 2010-04-23
> **The Mad Scientist said:**
> I upgraded to 9.10 from 9.04 during beta, and my wireless networking lost WPA capability, which effectively makes it worthless on my home network.  I assumed it was a beta issue, but it is still there with the release.  This issue occurred with my 8.10 to 9.04 upgrade, as well, but was fixed about a month after release with a patch.

From the info I can gather, it appears the orinico driver is being incorrectly used (orinico does not support WPA).  Blacklisting orinoco leads to a hang on boot.  Here is the current info:

IBM T30 Laptop
512MBytes RAM
Xubuntu 9.10 release (clean install)

lspci gives:
02:02.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)

lsmod shows:
orinoco_pci             4700  0 
orinoco                63600  1 orinoco_pci

Any hints on how to solve this?


Get a Belkin MIMO G USB Wifi, they are about 20 dollars at amazon, and they work great with 9.10 . 

Here I'll give you a link (the second one is the general search): 

[http://tinyurl.com/248v379](http://tinyurl.com/248v379)
[http://tinyurl.com/24v56zu](http://tinyurl.com/24v56zu)

---

