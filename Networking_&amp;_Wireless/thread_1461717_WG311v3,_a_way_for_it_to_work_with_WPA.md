---
title: "WG311v3, a way for it to work with WPA?"
date: 2010-04-24
forum: Networking &amp; Wireless
---

### Post by jerome1232 on 2010-04-24
The card, WG511v3 Netgear, chipset is 88w8335 Libertas manufactured by Marvell.

Marvell has Linux drivers just none for this specifc chipset.

I got it working with the old xp 64 bit drivers via ndiswrapper. Unfortunately it will not auth using wpa.


The reason I'm using that version is because I can't figure out how to get the inf files out of the current one I downloaded. I ran it via wine to get files extracted out of the .exe, but no inf files came out, just a bunch of other gunk. I am hoping maybe the newer update drivers for Windows 7 will help me out.

Has anyone been able to get this card to auth with wpa? Any idea's on how to obtain a more up to date driver file?

---

### Post by jerome1232 on 2010-04-24
Okay apparently I had given up to soon, a fresh try yielded results.

I poked around in my .wine directories some more and found the inf file in

~/.wine/drive_c/windows/inf/wg311/x64/netmw13c.inf

Loaded that into wine, removed the old driver, adjusted my router to use wpa psk and....

it works!

---

