---
title: "Circular dependancy while trying to get modem to work"
date: 2009-07-26
forum: Networking &amp; Wireless
---

### Post by rug77 on 2009-07-26
Hi all,

I'm trying to get 9.04 installed on my father in law's old Acer 212TXV.  All OK bar the modem.

Much downloading and so forth later, I reached a point of getting a "patch-alsa 24 patch not found" error while trying to make the driver.

It seems that I need build-essential on the machine, so I started getting .deb packages via a usb-drive from my machine.

Slow process.  Download .deb ... copy across ... run ... find it needs another package first ... get that ....... repeat forever !

Finally hit a problem.  I need g++-4.4 to create libstdc++6-4.4-dev, and I need libstdc++6-4.4-dev to create g++-4.4.  Screenshot attached.

I'm trying to make the ali 5451 modem work.

If I'm heading in the wrong direction, can you please let me know.  I am (I think !) trying to compile snd-ali5451-modem to work with the gnomeppp and wvdial thingies.

I hope someone can help - it's been the best part of a week so far ...

Matt

---

