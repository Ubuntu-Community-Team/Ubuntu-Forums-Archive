---
title: "Issues with Intel X3100 graphics chipset"
date: 2008-06-24
forum: Multimedia Software
---

### Post by vmayer on 2008-06-24
I am running Ubuntu on a Toshiba Tecra M8 with an Intergrated Intel Graphics Media Accelerator X3100 chipset. Output of my compiz-check:

[SIZE="1"]Distribution: Ubuntu 8.04
Desktop environment: GNOME
Graphics chip: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
Driver in use: intel
Rendering method: AIGLX

Checking if it's possible to run Compiz on your system...

Checking for texture_from_pixmap... [ OK ]
Checking for non power of two support... [ OK ]
Checking for composite extension... [ OK ]
Checking for FBConfig... [ OK ]
Checking for hardware/setup problems... [ OK ][/SIZE]

First of all, I know now that Intel chipsets are bad w/ Linux, but I bought this computer w/ the intention to run Vista and just recently converted to Linux.

That being said, my problem is that my computer would freeze up whenever I tried to run 3D applications (ie. games like Glest, Supertuxkart).  To try and fix this, I turned off Compiz (System/Preferences/Appearance/Visual Effects = None), and that actually worked. Or, at least made it possible to run those games w/o crashing every time.  But I want to know:
(1) WHY was it crashing w/ Compiz on? and
(2) How can I know if my graphics chipset is optimally configured?

Because I eventually want to do some more serious 3D stuff (on the level of Autodesk Inventor if that's possible through Wine), which worked (as well as could be expected w/ X3100) when I had Vista.

---

### Post by unoodles on 2008-06-24
It seems that you problems are from a *ONE YEAR* old bug.
[https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/120834](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/120834)
It seems that the solution is coming. My guess is that by intrepid (8.10) this will be fixed.

---

### Post by vmayer on 2008-06-24
I found the following proposed solution on the site unoodles directed me to. **Should I give it a try?** Or is this not relevant/ not going to work?
If it works (the only way I will know is by re-enabling Compiz and trying to run those games again), I will post it to the thread as a confirmed solution.

Bela MIHALIK wrote:
I got some help on forum that i mentioned above ([https://bugs.freedesktop.org/show_bug.cgi?id=11847](https://bugs.freedesktop.org/show_bug.cgi?id=11847)), and i can use mesa_7_0_branch now.
It is working on my system. I can use blender without crash, and it is fast.
I think this bug is fixed.

 ----- sources & compile process -----

 # git clone git://anongit.freedesktop.org/git/mesa/drm
 # cd drm
 # make install
 # make -C linux-core install

 # git clone git://anongit.freedesktop.org/git/xorg/driver/xf86-video-intel
 # cd xf86-video-intel
 # make install

 # git clone git://anongit.freedesktop.org/git/mesa/mesa
 # cd mesa
 # git checkout -b mesa_7_0_local origin/mesa_7_0_branch
 ...edit configs/default file
 INSTALL_DIR=/usr
 DRI_DRIVER_INSTALL_DIR=/usr/lib/dri
 # make linux-dri-x86-64
 # make install

---

