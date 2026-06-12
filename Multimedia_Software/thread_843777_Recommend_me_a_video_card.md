---
title: "Recommend me a video card?"
date: 2008-06-28
forum: Multimedia Software
---

### Post by cereal killer on 2008-06-28
Ok, here's the issue. I got a PC with an ancient Radeon 7500 card (AGP), and EnvyNG cannot detect and install the drivers. What I want to do is use the dual monitor feature, but it won't allow me and gets really screwed up -- I see a piece of the screen on the TV while the rest is cut off -- and I don't see anyway to adjust this. This runs way above my measly knowledge of Ubuntu.

My other PC runs a Geforce 8600GT and everything is perfect once EnvyNG installs the drivers. So I'm looking for a cheap (under $50 hopefully) nvidia AGP card that will work well with EnvyNG and must have at last 1 DVI input.

Is this a possibility?

---

### Post by extigyro on 2008-06-28
GF 8400GS Silent, 256MB Asus EN8400GS Silent/HTP/256M, DDR2 PCI Express TV Out
GF 7200GS, 256MB Sweex, PCI Express, TV Out
GF 8400GS 512MB 64bit DDR2 PCI Express, DVI, TV Out

...... 

But it MUST be nvidia absolutely for sure ! No ATI cards !

---

### Post by SeePU on 2008-06-29
Those are PCI-e (PCI Express) choices, aren't they?

To OP, try to find an Nvidia 7900GS but if too expensive, look for a 7600GS AGP card.   They both have DVI inputs.  I would look for one used or on ebay as they're overpriced whenever you find them in stores.

---

### Post by cereal killer on 2008-07-01
How about the NVIDIA GeForce MX440, I can get it for real cheap.

Any clue how compatible it is? My main goal is to run dual monitors with one of them being a TV via DVI - HDMI cable.

---

### Post by alegallo on 2008-07-01
Well, no doubt you can get it for cheap, it's quite a different card from the ones above ;)

I'm going great with a Ti4800SE, but I guess any card from GeForce 4 onwards should do fine for your needs

---

### Post by Melcar on 2008-07-01
That card you have is not supported by fglrx, that's why Envy does not recognize it (no drivers to install).  You need to use the "radeon" driver.  It's included in Ubuntu and should be the default module that loads for the card (unless Ubuntu is loading Mesa for some reason).  Check here for configuration options (you can also type "man radeon" in the terminal):

[http://www.x.org/wiki/radeon]("http://www.x.org/wiki/radeon")
[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

