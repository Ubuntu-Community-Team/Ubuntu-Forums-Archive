---
title: "NVidia driver issues"
date: 2009-05-06
forum: Multimedia Software
---

### Post by peyre on 2009-05-06
I'm using an older computer--I'm hoping to buy a new one before too long, but I'm the sole breadwinner and we have two small children, so money has been kind of tight.  So for the time being I'm getting by (actually pretty handily, thanks Xubuntu!) on this older machine.  But there's an issue with the video card.

My graphics card identifies itself as "nVidia Corporation NV5 [RIVA TNT/TNT2 Pro] (rev 15)".  It's known that the proprietary driver for some older nVidia cards (including this one) is broken in the latest Linux kernel.  NVidia released an updated experimental driver to try to get around this.  I've tried installing it several times, in 8.10 and 9.04, always without success.  It says it installed successfully, but when I reboot after updating xorg.conf as directed, I'm told the graphics is misconfigured and it puts me back to a generic driver.

I've tried using EnvyNG, which detects and installs the right driver (it sets up the latest stable version), but on reboot I get the same thing.

So I've tried Nouveau with 9.04, but after install it never seems to do anything.  My xorg.conf file still shows plain vanilla lines:
```
Section "Device"
  Identifier      "Configured Video Device"
EndSection
```and so on.

So I guess I'm still using the nv driver, which works ok, except it doesn't support 3D so most of my kids' educational software doesn't work on it.  Can anyone shed some light on the situation?  (I know I'm a little hazy on some of the details, but it's been a convoluted process.)

The way it looks now, I guess I have three options: grin & bear it, buy an updated graphics card (if I can find the right AGP card), and buy a new computer.  Thoughts anyone?

---

### Post by interestinfellow on 2009-05-12
you can pick up a decent used AGP card on ebay for $10 or $15.  it's what I would do. got any friends with old hardware lying around (by friend, I mean someone who feels compelled to purchase overprice cutting edge crap, and by old hardware, I mean 6 mos or so)?  Good luck.

---

### Post by peyre on 2009-05-13
Hey thanks!  Turns out a friend went out and got me a more advanced video card that my MoBo will support as an early birthday present.  (It came in the mail this afternoon.)  So looks like I've gone with the second option for the time being...I'm testing it out now.  If nothing else, this card actually DOES appear in Hardware Drivers, unlike my old one.

---

