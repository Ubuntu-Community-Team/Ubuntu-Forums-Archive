---
title: "Strange desktop when booting from live USB/CD"
date: 2009-06-12
forum: Mythbuntu
---

### Post by dumb on 2009-06-12
Hi,
I've created a live USB, using unetbootin. When I boot, I get the Mythbuntu splash screen allright, but when it starts up xfce4 desktop, all I get is strange "garbage" rolling up my screen. I've tried connecting the computer, to my monitor and my LCD TV, both via DVI but they both got the same result. This means  that I can't install mythbuntu.

The hardware I use, is a VIA Epia EX10000 Motherboard, which uses the CX700M2 graphics chipset.

The computer previously ran Minimyth with no complaints and all worked flawlessly. But now I have to go over to wireless network, and thats not supported by minimyth, so I would give MythBuntu a try. But for now, with out any success...can anybody help?

Regards
Thomas

---

### Post by dumb on 2009-06-15
Ok, solved the problem, by changing driver in xorg.conf to "vesa" and then starting up a new X and ran the install from there.

---

### Post by mulluysavage on 2010-02-21
is there a how-to on making a mythbuntu live usb?

---

