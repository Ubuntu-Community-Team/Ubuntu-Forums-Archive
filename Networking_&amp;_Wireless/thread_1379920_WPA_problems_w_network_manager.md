---
title: "WPA problems w/ network manager"
date: 2010-01-13
forum: Networking &amp; Wireless
---

### Post by jjmerelo on 2010-01-13
Hi,
I have a Sony VAIO VGN SR29VN with ubuntu 9.10; I am trying to make a wifi connection through WPA work, to no avail. WEP and open connections work correctly, but when I try to connect to a WPA network using TTLS via network manager, y get errors of this type:
> Current regulatory domain updated by AP to:ES

preceded by lots of "leaving channel xxxx intact" and followed by "disassociating by local choice". 
This Sony is using an Intel 5100 wifi; any idea of what's going on or how to fix it? 
Thanks!

JJ Merelo

---

### Post by changingstate on 2010-01-13
The laptop is disconnecting because the AP is reporting it's set up for spanish (ES) transmission laws and your laptop isn't and for whatever reason, won't switch over.

A little reading material here may prove helpful : [http://localloop.co.za/2009/06/getting-the-new-linux-wireless-regulatory-domain-stuff-to-work/](http://localloop.co.za/2009/06/getting-the-new-linux-wireless-regulatory-domain-stuff-to-work/)

There's been some reports of some kernel modules and some kernel versions being daft with this stuff on google. Letting us know what you're running would be useful if you'd like further assistance.

---

### Post by jjmerelo on 2010-01-14
Thanks for the link, will try and report back. I'm using right now an updated version of 9.10, can look for the kernel version if needed.

Cheers

JJ

---

### Post by jjmerelo on 2010-01-19
It really does not work. Any other idea?

JJ

---

