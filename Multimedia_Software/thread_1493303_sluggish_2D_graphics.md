---
title: "sluggish 2D graphics"
date: 2010-05-25
forum: Multimedia Software
---

### Post by KrisWragg on 2010-05-25
I've just installed kubuntu 10.04 x64 and I'm slowly working through lots of little niggly problems that I'm having getting it all set up.

My graphics seem VERY sluggish doing things like opening and closing windows, popping up menus etc.

I have an Athlon II 250 3.0ghz processor, 2GB RAM and onboard graphics ATI HD2100 (740G chipset).

I tried to get the proprietary graphics driver installed to see if that made any difference but it wouldn't recognise the onboard graphics, a bit of googling seems to suggest they have actually dropped support for this model?

After removing the proprietary stuff it seems even more sluggish than it did before.

Was wondering if anyone can perhaps give me some tips on things I can tweak or look at to try and improve matters?

Many thanks, I've ditched Windows now and am trying my hardest to try and be happy using linux but niggly things like this and spending half a day trying to get flash working correctly are enough to drive a man insane!

---

### Post by efflandt on 2010-05-26
You might try nomodeset kernel boot option to see if that works any better than the new kernel mode setting (KMS) video driver.  That helped with my older ATI X1300 video (and fixed inability to suspend/hibernate).

You might also try disabling Visual Effects (None) to see if that helps any (under Appearance).

---

### Post by KrisWragg on 2010-05-26
Hi, is that related to a fix I tried that said to do this:

```
Add radeon.modeset=1 to the end of the line GRUB_CMDLINE_LINUX_DEFAULT=.  
```Do I just substitute radeon.modeset=1 with nomodeset ?

---

### Post by Yellow Pasque on 2010-05-26
Make sure you really removed fglrx: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

You can then try the xorg-edgers PPA: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

