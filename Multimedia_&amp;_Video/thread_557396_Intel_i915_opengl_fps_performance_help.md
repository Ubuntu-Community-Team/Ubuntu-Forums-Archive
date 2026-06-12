---
title: "Intel i915 opengl fps performance help"
date: 2007-09-22
forum: Multimedia &amp; Video
---

### Post by chroncile on 2007-09-22
I need help installing my intel linux graphics.
It get's this error :

```
Compiling new agpgart module...

ERROR: AGPGART module did not compile

Compiling DRM module...

ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.

```

Please someone help me :(

---

### Post by chroncile on 2007-09-22
Bump, come on someone please help me :(

---

### Post by rdlf0512 on 2008-01-25
I don't know what you were doing, but if your trying to install some new version of i915 driver, you will need to get a newer version of xorg that can be downloaded from here: [http://xorg.freedesktop.org/archive/X11R7.3/src/xserver/xorg-server-1.4.tar.bz2](http://xorg.freedesktop.org/archive/X11R7.3/src/xserver/xorg-server-1.4.tar.bz2) [direct link to the file]

But I tell you one thing: intel has poor opengl support. I experienced this fact when running war craft III on winxp and Linux Ubuntu: on winxp it ran just fine but on wine (Ubuntu) it sucks. What I'm trying to say is you will not get too far with this i915.

I have a nobo with this i915 and I am going to sell it, due to some mistakes. Anyway, I will never buy another intel product again (including intel gma-based-nobos and intel processor) because they don't support us.

Anyway, try to ./configure xorg-server. It will require some packages. Install the packages from synaptic or look for it on [http://www.paldo.org/](http://www.paldo.org/) . When you are done, build the installer for xf86-video-intel (./configure, make) and then run the installer (make install) from the terminal.

---

