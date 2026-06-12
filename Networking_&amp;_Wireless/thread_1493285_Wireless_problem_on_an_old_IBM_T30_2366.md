---
title: "Wireless problem on an old IBM T30 2366"
date: 2010-05-25
forum: Networking &amp; Wireless
---

### Post by The Spork on 2010-05-25
Hi everyone, I'm new here and sort of new to linux.

I have a problem with my old T30 that I now use as an xubuntu machine, in that I can't seem to get the wireless working with WPA\WPA2 encryption (neither show up as options in network manager).

It has an IBM high rate wireless LAN with modem II card which has the Intersil Prism 2.5 chipset (that's what shows up in lspci).  A quick look at thinkwiki shows that this card uses the orinoco-pci drivers, which do not currently support WPA, but can also use hostap. After a bunch of trying to find info on what to do here and elswhere, some people said to blacklist orinoco and just use hostap, but many people say that just causes the system to hang.

So my question is this, what do I do? is it possible to get this working with the native drivers somehow, or do I use ndiswrapper?  Should I just go buy a usb/pcmcia adapter?  I would like to stick with the native drivers if possible and I really don't want to spend much money on this old thing.

Any help is appreciated. Thank you.

---

### Post by The Spork on 2010-05-26
Bump

---

### Post by The Spork on 2010-06-01
Is anyone available to help me with this?

---

### Post by chili555 on 2010-06-08
Please see: [http://ubuntuforums.org/showthread.php?t=1498434&page=3](http://ubuntuforums.org/showthread.php?t=1498434&page=3)

Especially see post #24 and #26.

---

