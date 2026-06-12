---
title: "Radeon 3870 X2 Problem"
date: 2010-04-12
forum: Multimedia Software
---

### Post by Dan09 on 2010-04-12
Hi everyone! I apologize if this has been addressed elsewhere (I haven't found anything yet), but I was wondering if you guys could help me out with a annoying problem I've been having.

I have two Radeon HD 3870 cards running in Crossfire in my notebook and have just installed a ubuntu 9.10. For some reason whenever I try and enable desktop effects it fails on me.  When done through the "Appearance" GUI method it simply says "Desktop Effects cannot be enabled" and reverts back to None.

Here is the output compiz gives when I try running it in the Terminal :

```
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1440x900) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: xterm 
no xterm found, exiting
```I'm assuming it's using the open source "radeon" drivers and not the propietary "fglrx" driver. I tried looking for the fglrx driver in Synaptic but it's no where to be found.

Any ideas on what I'm doing wrong? Thanks very much!

EDIT : Hey all, another problem has just come up. I tried activating the proprietary ATI driver listed under "Hardware Drivers" after I rebooted however, everything went black.

Ubuntu starts up and everything (with the little drumming sounds that plays when the login screen pops up) but the screen is entirely black. GAH!

---

### Post by Dan09 on 2010-04-12
Sorry for the double post; but I'm kind of desperate.

Does anyone know how to switch from the fglrx driver to the working "radeon" open source one via the console?

X isn't showing up at all thanks to the bugged proprietary drivers.

HEELLLPPP!

---

### Post by Dan09 on 2010-04-15
Hey all, I ended up reinstalling Ubuntu and am back with the semi-working open source drivers (hey, at least they work).

Does anyone know if I could possibly trick Ubuntu into using only ONE card instead of 2? That way I could avoid all these problems with using the proprietary drivers and get 3D support.

Thanks a lot in advance! :)

---

