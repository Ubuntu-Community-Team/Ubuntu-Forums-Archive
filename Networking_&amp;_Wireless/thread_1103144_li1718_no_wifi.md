---
title: "li1718 no wifi"
date: 2009-03-22
forum: Networking &amp; Wireless
---

### Post by t595david on 2009-03-22
noob neets guidance, fujitsu/ siemens alimo li1718 laptop. with a     "software" controlled wifi switch . googled and found a file named.acerhk-0.5.35. this is supposed to be compatable with my laptop.more googling revealed that "acerhk" could be added by using syaptic package manager.the hardware manager is showing the drivers are there , ifconfig , has a line in it saying "power maagment off".
so as i see it , the card needs enabling some were else , or the acerhk isnt working.

any advice appreciated..............no smart comments  about going back to windows needed!

---

### Post by abyssius on 2009-03-22
> **t595david said:**
> noob neets guidance, fujitsu/ siemens alimo li1718 laptop. with a     "software" controlled wifi switch . googled and found a file named.acerhk-0.5.35. this is supposed to be compatable with my laptop.more googling revealed that "acerhk" could be added by using syaptic package manager.the hardware manager is showing the drivers are there , ifconfig , has a line in it saying "power maagment off".
so as i see it , the card needs enabling some were else , or the acerhk isnt working.

any advice appreciated..............no smart comments  about going back to windows needed!

My advice is to post your actual ifconfig output. More important info would be if ifconfig shows an IP addres or not. Also, ```
lshw -C network
``` and ```
iwconfig
``` will give support volunteers a better idea of what's going on.

---

