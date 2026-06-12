---
title: "How can I get back from fglrx to ATI driver?"
date: 2006-12-11
forum: Multimedia &amp; Video
---

### Post by Chris11 on 2006-12-11
I had my Radeon 9000 Pro working on Dapper with about 1000 FPS following the instruction guide for my graphic card. Last week I updated to Edgy - everything went cosy unless the graphic card.

The fglrx 8.28.8 driver (included in edgy) did not work, I don't remember what error message I got during startup. I deinstalled  fgrlx and got surprisingly! with the ATI driver 3D with 750 FPS. I had about 1000 FPS on Dapper.

I thought to try it once more toady an used the Ubuntu Edgy Installation Guide. [http://wiki.cchtml.com/index.php/Ubu...allation_Guide](http://wiki.cchtml.com/index.php/Ubu...allation_Guide)

Now the fgrlx works but with no 3D:

> fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

> glxinfo | grep direct
Xlib: extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

I thought to go back to the ATI driver using the old xorg.conf, but the ATI driver is not found any more on my system - where has it gone? Is there a way to make the fglrx run ore to go back to the ATI? 

any help is appreciated.. 

Chris

---

### Post by Chris11 on 2006-12-11
I went over it once more and found out that I had a missing entry in the xorg.conf

> Section "Extensions"
Option "Composite" "Disable"
EndSection


I added the entry and get now the following..

> fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

glxinfo | grep direct
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect


but still no 3D...

I load

> 
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
psmouse
fuse
fglrx


I'm not sure if something is wrong here...

---

### Post by Chris11 on 2006-12-12
Bump! ](*,)

---

### Post by praxis22 on 2006-12-12
This page should sort you out:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Essentially:

Good bye fglrx, welcome open source :)

Fglrx is the name of the official, proprietary, Radeon driver from ATI. It conflicts with the open source "radeon" driver. When "fglrx" is loaded at boot, X will be able to start using the "radeon" driver but "Direct Rendering" will be disabled. This results in a severe performance reduction. If you previously installed the proprietary "fglrx" driver then removing it is highly recommended if you wish to use the radeon driver. This can be done with:

sudo rmmod fglrx

The libGL.so in /usr/lib might also still be the version installed by xorg-driver-fglrx. You can check that very easily: Just run:

$ glxinfo |grep vendor

If you see: client glx vendor string: ATI, then the libGL.so is still from ATI. Just remove the xorg-driver-fglrx package and make sure libgl1-mesa-glx and libgl1-mesa-dri are installed:

$ sudo apt-get remove xorg-driver-fglrx; sudo apt-get install libgl1-mesa-glx libgl1-mesa-dri

More on the page itself.

---

### Post by Chris11 on 2006-12-12
Thanks, that made everything smooth...

Chris

---

### Post by warjowuch on 2007-02-13
Not for me, I have installed the open driver after using fglrx for a while, removed it (completely) customized my xorg.conf but it does not do anything. It still says client glx vendor string: ATI

That sucks, while I reïnstalled all those mesa and xserver-xorg-driver-ati packages...

What the heck?? Can some-one help this poor guy?

Actually, I used the xorg.conf which provided 3d, directly from the edgy livecd. So it is not in the xorg.conf, but somewhere in some left-behids from the fglrx-installer I think... (?)

---

