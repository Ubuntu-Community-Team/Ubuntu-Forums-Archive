---
title: "NetGear: almost there after hours of pain"
date: 2009-04-12
forum: Networking &amp; Wireless
---

### Post by n2stc on 2009-04-12
After hours of struggling and reading posts it almost works.  My NG MA521 card is recognized, gets an IP address and the link light comes on!  I just can't access anything through it.  Frankly I'm TIRED OF SEARCHING.  Anyone have a suggestion or can point me to a link?

Thanks,
Stan

---

### Post by n2stc on 2009-04-12
I should mention I am running UBUNTU, on a COMPAQ laptop.

---

### Post by lisati on 2009-04-12
Buried in the information at [http://kb.netgear.com/app/products/model/a_id/2493](http://kb.netgear.com/app/products/model/a_id/2493) I found [ftp://downloads.netgear.com/files/MA521_Refguide.pdf](ftp://downloads.netgear.com/files/MA521_Refguide.pdf)
It looks like you might have to use ndiswrapper or similar to install a driver. Since I've not done that myself, I'll have to pass the reins on to someone else for tips.

---

### Post by n2stc on 2009-04-12
> **lisati said:**
> looks like you might have to use ndiswrapper or similar to install a driver. Since I've not done that myself, I'll have to pass the reins on to someone else for tips.
 
Yes, That's how I got this far.  Thanks for the reply and your time.

---

### Post by geoff07 on 2011-07-01
I realise that this is a very late post, but for the benefit of anyone still searching to make this card work, this is the current state as of July 2011:

To make the MA521 Netgear WiFi card work under Ubuntu 11.04

- download the XP version of the realtek 8180 wifi driver (NOT the Vista or any other version) from the Realtek web site. Unzip and put the three files into a suitable directory under Home. The MA521 uses the Realtek chip.
- ensure that NDISWRAPPER is installed, including the -utils files and the ndisgtk GUI 
- access the GUI under System/AdminWindowsWirelessDrivers
- insert the MA521
- using the GUI add the NET8185.INF driver from the directory in which you put it
- the power light on the card should already have been on, now the Link light should also light
- using the NetworkManager applet, specify the security as necessary
- enjoy

This worked for me once I realised that it had to be the XP driver.

---

