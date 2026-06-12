---
title: "FSC Amilo 2727 Wifi issues with 9.10"
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by foo-monger on 2009-10-31
Hi,

I hope someone can help me with this problem.  I have a FSC Amilo 2727 laptop which has a softkey setup to activate the wifi.  This doesn't work in Ubuntu but I managed to get the wifi on using the advice in this link with 9.04.   [http://ubuntuforums.org/showthread.php?t=986288](http://ubuntuforums.org/showthread.php?t=986288)

I've just upgraded to 9.10 and hoped the wifi would still work but it doesn't and the older solution doesn't help either.

I'm not bothered about the softkey activation, just a permanent wifi connection will do.

Any advice will be appreciated.

Thanks in advance.

---

### Post by queBurro on 2009-11-21
I'm in the same boat: 9.10 on a 2727 try this:

> 1) get rid of the ath_pci module (sudo rmmod ath_pci)
2) activate acer-wmi module (sudo modprobe acer-wmi)
[http://swiss.ubuntuforums.org/showthread.php?t=986288&page=3](http://swiss.ubuntuforums.org/showthread.php?t=986288&page=3)

sorry, think I meant "acer_wmi" - can't remember at the mo'

---

