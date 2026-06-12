---
title: "3D effect of ATI X1400 is really slow under Ubuntu 9.10"
date: 2009-10-23
forum: Multimedia Software
---

### Post by hkenneth on 2009-10-23
I switched from fglrx driver to the opensource ati driver when upgrading from 8.10 to 9.10 beta. Before upgrading I totally removed the fglrx driver (using apt-get uninstall --purge) and the system automatically using the opensource one.

After upgrading, 2D rendering including xv is decent. HD video playing is smooth. And for Google Earth, 3D effect is also very fine.

But for some other applications, 3D effect is extremely slow, including Compiz, Blender, and Mathematica.

What makes me really confused is glxgears shows about 6000 fps for my video card. But after I open compiz, it reduces to 50fps.

I checked the status of the driver, which showed that direct rendering was opened. I don't know if it is just because the poor support of 3D for my X1400 card by the opensource driver, or it is due to improper configuration.

(xorg.conf is the default setting for the opensource driver, which actually contains almost nothing. EXP is opened I guess.)

> GL_RENDERER   = Mesa DRI R300 (RV515 7145) 20090101 x86/MMX/SSE2 TCL
GL_VERSION    = 1.5 Mesa 7.6
GL_VENDOR     = DRI R300 Project


---

### Post by Harpalus on 2009-11-01
I'm experiencing a similar problem. Unfortunately, playback on mplayer falters frequently, and videos will simply stop playing, and/or the sound will cut out. It doesn't seem to matter what quality/codec the video is.

I never need much 3D, but Wine/World of Warcraft doesn't work for me.

Coincidentally, I also came from 8.10, albeit via a clean install. This experience is making me want to move back to it, because at least I could game and watch videos on the old release..

Can anybody offer advice?

---

### Post by fallingleaf on 2009-11-02
I have the same issue.  This is on a clean install of Karmic with an X1300 card.  I was using Jaunty with the open source driver before and didn't have this problem.  Even without compiz enabled, if a second user logs in the rendering for the second user is unbearably slow.

---

### Post by skitheo on 2010-05-04
> **fallingleaf said:**
> I have the same issue.  This is on a clean install of Karmic with an X1300 card.  I was using Jaunty with the open source driver before and didn't have this problem.  Even without compiz enabled, if a second user logs in the rendering for the second user is unbearably slow.
I too have the same experience with the second user being extremely slow with either Compiz or MetaCity. Makes the "switch user" functionality practically useless. Tried all the combinatorics of 1st & 2nd users using Compiz or MetaCity. Same result, except if both use Compiz, returning to second user with Ctrl-Alt-F9 will result in a blank white screen until I "restart gdm".

Karmic, AMD64, 10GiB RAM, 2x AMD Opteron 270 dual core, ATI FireGL v3400 (R530 w/ 128MiB RAM) "radeon" driver.

---

### Post by skitheo on 2010-05-04
Supposedly this is fixed in Lucid Lynx 10.04LTS if KMS is activated by default:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/473098](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/473098)

I guess I'll have to upgrade and try it out ;-)

---

