---
title: "HP dv5*** series ATI 200M Issue"
date: 2006-07-05
forum: Multimedia &amp; Video
---

### Post by Bayleo on 2006-07-05
Anyone care to elucidate on this portion of the wiki?

[I] HP Notebook dv5029us / zv6000

If you have an HP Notebook Computer (or Compaq) such as the HP dv5029us or zv6000 series, it is needed to modify the BIOS configuration. It seems for some reason using sideport memory (the card's onboard memory only) leads to an apparent system crash although the logs show successful initialization of DRI. It is needed to run the BIOS setup screen, go to memory options, and select UMA+Sideport memory and assign a value to it (I assigned an extra 128M from the system RAM). Boot the computer and the fglrx driver will work. FGLRX version is 8.24.8 on an i386 Ubuntu Dapper install.

    * Ubuntu FGLRX drivers 8.25.18, do not work properly on the dv5029us (Radeon Xpress 200M) as of this writing (5/30/2006). It is needed to revert to 8.24.8 for this specific computer in order to get proper 3D acceleration, and 2D with no tearing off. 

    *
          o ATI Driver 8.26.18, does not work with the Radeon Express 200M. Some HP/Compaq laptops only have working 3D support with ONLY UMA video memory( Sideport+UMA won't work ). This is due to a 1 year old flaw in the ATI driver. If you want to use your onboard/Sideport memory, you can only get 2D support by adding [ Option "no_dri" "yes"] to the fglrx driver section of /etc/X11/xorg.conf 
[/I]

I attempted installing 8.26.18 several times and both times was stuck with a blank screen lockup immediately after booting, after reading this I attempted to allocate system memory to the sideport within the BIOS to no avail.  Does this mean I should try reverting back to 8.24.8, or am I SoL for 3D acceleration?

Soooo, anyone else trying to deal with this?

---

### Post by d-E-a-D on 2006-07-05
Ok, after more than 10 formats and thousand tries to make it work, i get 8.26 drivers working on my hp pavilion dv5172 with ati radeon Xpress 200m.
***_I'm using UMA+SIDEPORT 128Mb._***
It gives me the right fglrxinfo:

OpenGL vendor string: ATI technologies Inc.
OpenGL renderer string: RADEON XPRESS 200M Series Generic
OpenGL version string: 2.0.5879 (***_8.26.18_***)

Now my issue is that glxgears and fglx_gears hangs when i try to run it _***but things like screensaver and games do it great on OpenGL and fps.***_ but it is unstable. sometimes crash, others not.

The worst issue is that it seems that it doesn't refresh the image, everything just is it seems that the windows are over ones of the others, I see the images overlapped, icones disappears when I open something over them and closes.
To read console i have to underline the mouse over the letters. but if i maximize the console i can read it all great.

Now the steps.
Fresh Install of Ubuntu 6.06
update
distro-upgrade
restart
follow this thread but ***_WITH 8.26.18 DRIVER DOWNLOADED FROM ATI_***:
[http://www.ubuntuforums.org/showthread.php?t=199421&page=2&highlight=ati+8.24+200m]("http://www.ubuntuforums.org/showthread.php?t=199421&page=2&highlight=ati+8.24+200m")
restart

For now i can't go further... does anyone goes further than this with 8.26.18 drivers?

NOTE: 8.24.18 drivers worked for me with the thread i said. but i can't get XGL and COMPIZ working. And with fglx_glxgears i just see one piece rolling, the others don't appear like in glxgears.

If someone have this 200M card working well and with XGL and COMPIZ please give us a HOW-TO step by step !!!!

SORRY MY BAD ENGLISH.

Cumps

---

### Post by Bayleo on 2006-07-05
Your testimony is heartening d-E-a-D... at least I know this is possible.

I'm going to continue reformatting and making attempts at this until I get it to work (I'm on a 5000dv w/ a 200m).  I might try grabbing the new kernel before the next attempt at installing the drivers.

Soon as I can get this thing to work I'll try to help you tweak it.

---

### Post by d-E-a-D on 2006-07-07
now i'm using 8.24 again... 8.26 it's very unstable, follow the link i said before and install 8.24.

Cumps

---

