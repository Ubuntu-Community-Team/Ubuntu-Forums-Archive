---
title: "Help! Nvidia 177.82 upgrade broke my display (Intrepid)"
date: 2009-01-07
forum: Multimedia Software
---

### Post by MistralWind on 2009-01-07
Hi, everyone! I have a problem I'm hoping one of you brilliant folks can solve. :)

I'm running Intrepid Ibex. I have an GeForce 8500 GT graphics card and I'm using Compiz Fusion (or at least I was!). Everything was mostly functional under Nvidia driver 177.81.

After an automatic update to driver 177.82, Compiz stopped working, a little desktop program I use (Rainlendar) got a weird black border around it, and all of my GL screensavers stopped working. Before the "upgrade", there was also a glitch from KDE3 where I still had the Mac style toolbar, but now, I have no toolbars at all when I run Dolphin and other utilities that made use of it. Compositing is broken now, too, just for the record.

I've tried rebooting. I've also tried reinstalling the drivers and anything else named Nvidia from the repository.

Can someone please help? This is driving me crazy.

---

### Post by MistralWind on 2009-01-07
This is what I get when I run compiz --replace:

> justme@justmy-land:~$ compiz --replace
Checking for Xgl: not present.
Detected PCI ID for VGA:
Checking for texture_from_pixmap: Segmentation fault
not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: Segmentation fault
not present.
aborting and using fallback: /usr/bin/kwin
kwin(7493) KDecorationPlugins::loadPlugin: kwin : path  "/usr/lib/kde4/kwin3_crystal.so"  for  "kwin3_crystal"

---

### Post by MistralWind on 2009-01-07
Anyone? Please? I'm getting desperate here. If it helps, I get this message when I go into Nvidia Xserver Settings and select OpenGL/GLX Information:

> Fail to query the GLX server vendor.

---

### Post by memories on 2009-01-07
How did you install the nvidia drivers? I personally recommend going with Nvidia's own drivers (see this [http://ubuntuforums.org/showthread.php?p=6512030#post6512030](http://ubuntuforums.org/showthread.php?p=6512030#post6512030) ). I've never had a problem with them. 

Run **glxgears**. Does it work? Run **glxinfo** and paste the output here (minus the numbers and useless info on the bottom). You probably just need to enable glx/direct rendering in your Xorg.conf.

---

### Post by MistralWind on 2009-01-07
Oh, thank goodness! Someone found this! :D

When I try to run glxgears, I get this:

> Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual

When I run glxinfo, I get this:

> name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
3 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Segmentation fault

As for how I installed the driver, I did it automatically. When I upgraded to Intrepid and it asked me about restricted drivers, I just picked one from the list. Today, 177.82 came with my regular automatic updates this morning, so I didn't think much of it... until it hosed my system.

---

### Post by Chaos_Spear on 2009-01-07
Yeah, don't do it from the desktop environment.  I'm running an Nvidia 8600 GT, and when I first installed Kubuntu, I went with a text-based installer and then ran the shell script that Nvidia has on its linux driver page before I ever booted into KDE.  Later, I tried updating with one of the KDE utilities and it broke everything.

I suggest doing the same - go to [http://www.nvidia.com/object/linux_display_ia32_177.82.html](http://www.nvidia.com/object/linux_display_ia32_177.82.html) and download the package, then run it from terminal according to their instructions.

---

### Post by MistralWind on 2009-01-07
It took some doing, but since I'd heard good things about it, I decided to go ahead and install the 180.17 beta driver from the Nvidia site. Compiz is back, my screensaver is running, and everything is wicked-fast! So, thanks, guys, for suggesting just getting the drivers from the site directly. :)

---

### Post by gasto on 2009-01-07
I got the drivers from the site directly but got, a black screen :(

---

### Post by RJARRRPCGP on 2009-01-07
Possibly a mismatch between the kernel and the Nvidia kernel module. :(

Prepare to reinstall the Nvidia drivers. :(

---

### Post by MistralWind on 2009-01-07
> **gasto said:**
> I got the drivers from the site directly but got, a black screen :(
Did you uninstall the old driver first? (The instructions on the Nvidia site leave something to be desired.)

---

### Post by RJARRRPCGP on 2009-01-07
> **RJARRRPCGP said:**
> Possibly a mismatch between the kernel and the Nvidia kernel module. :(

Prepare to reinstall the Nvidia drivers. :(



If the above mentioned problem is true, you should see "ERROR: Unable to load the NVIDIA kernel module" or similar during the boot process.

---

