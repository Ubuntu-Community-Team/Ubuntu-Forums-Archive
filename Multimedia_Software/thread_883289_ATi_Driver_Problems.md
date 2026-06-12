---
title: "ATi Driver Problems"
date: 2008-08-07
forum: Multimedia Software
---

### Post by XkW on 2008-08-07
My oh my, the dreaded ATi Driver. No matter what I do, I can't get installed, I always get the dreaded BSOD (Black Screen of Death)at bootup. Thank god for recovery mode!
I have an ATi x800 256Mb AGP graphics card. Advice is very much appreciated!

~Kev

---

### Post by tuxxy on 2008-08-07
My only advice apart form try envy to install them is upgrade to an nvidia, it should run without fault.

---

### Post by XkW on 2008-08-07
Hehe, I don't really have money right now.... and envy doesn't work, but I will keep it open as an option ^_^. Anybody else have any advice that will prevent me from having to spend money on a new graphics card?

---

### Post by tuxxy on 2008-08-07
Well even if you get the drivers isntalled dont expect flawless graphics in 3D or for compiz either, I had to upgrade because of these too

---

### Post by XkW on 2008-08-07
Ehh, I'm not goin for flawless, I just wanna experiment with compiz a bit. As for gaming and such, well, thats what Windows is for ^_^

---

### Post by tuxxy on 2008-08-07
Well ye I use PS3 for them games but I mean even simple games like you may want to try eg tuxracer, tuxkart etc

---

### Post by justin99 on 2008-08-08
I had managed to get the ATI driver to work at one point, and I had similar issues.. I seem to remember that renaming my xorg.conf (in /etc/X11) file so a new virgin one was created got me partially up and running. I think certain configs there were crashing the driver. This was a long time ago and now I use nvidia. Try that, also take a look at the Xorg.0.log file in /var/log...

---

### Post by Melcar on 2008-08-08
Well if all you want to do is be able to run Compiz, the open source driver is more than enough for that.  Some gaming is possible as well.

---

### Post by oronte on 2008-08-08
What I did was get the files from the ati support website and I used the info at the Ubuntu documentation project to install it (google Ubuntu ati drivers to find it). The page suggested I disable textured video in my Xorg and now everything pretty much works - compiz and 3d games at the same time. As soon as I have some cash I'm going for an nvidia though.

---

