---
title: "Radeon HD4670 AGP  in 12.04 LTS?"
date: 2013-02-27
forum: Multimedia Software
---

### Post by eckz59 on 2013-02-27
Hey Ubuntu masters,

I have the AGP version of the Radeon HD4670 and am running Ubuntu 12.04 LTS in a Unity2D session.

Right now, I have the open-source radeon driver installed, I've upgraded to kernel version 3.6 to enable OpenGL 3.0 support, and I've done a dist-upgrade after adding one of the cutting-edge X PPA's in order to get Mesa 9.0. I've also added vblank_mode = 0 to my ~/.bashrc and I've set the option "SwapBuffersWait" to "false" in /etc/X11/xorg.conf. The output of glxinfo | grep OpenGL is as follows:

OpenGL vendor string: X.Org
OpenGL renderer string: Gallium 0.4 on AMD RV730
OpenGL version string: 3.0 Mesa 9.0
OpenGL shading language version string: 1.30
OpenGL extensions:

X.Org X Server 1.11.3

All of this so that I can play Counterstrike Source on Steam for Linux. There are no graphical errors, but the performance is TERRIBLE (10-12 FPS).

What are the correct Catalyst/fglrx drivers for me to be using for this HD4670 AGP card, now considered "legacy", on 12.04 LTS? I can downgrade the kernel.

Any help -- GREATLY appreciated. Thanks ahead

---

### Post by linuxuser21 on 2013-07-04
Bump.

Old thread, I know; but, I need the fglrx drivers for this card as well and I have yet to yield any answers.
To my understanding, [this]("https://launchpad.net/~makson96/+archive/fglrx?field.series_filter=raring") solution does not work.

At the bottom:
> "P.S. It was pointed to me, that Radeon HD4670 AGP card is EXCLUDED from the Legacy Driver support."

---

### Post by Yellow Pasque on 2013-07-04
>  I need the fglrx drivers for this card
It might be time to think about a new system...

---

### Post by linuxuser21 on 2013-07-05
> It might be time to think about a new system...
Haha, knew that was coming.  Long story short, it's being used on my first computer; I rebuilt it as a HTPC running XBMC.  Using older hardware on this build keeps the wallet (somewhat) safe and me entertained.

---

### Post by dannyboy79 on 2013-07-05
unfortunately I can't help with the HD4670 but I can tell you that I have an Nvidia 6200 (AGP) ([http://www.newegg.com/Product/Product.aspx?Item=N82E16814130635](http://www.newegg.com/Product/Product.aspx?Item=N82E16814130635)) which was only $32.99 and the legacy 96.41 nvidia drivers work with. You may get decent performance out of it for CS:Source

---

