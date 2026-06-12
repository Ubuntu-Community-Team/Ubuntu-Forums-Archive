---
title: "[SiS] 661/741/760 driver video problems"
date: 2012-08-26
forum: Multimedia Software
---

### Post by DocStrangeLove on 2012-08-26
I installed Ubuntu desktop 12.04 (alternative installation, the normal ver didn't work with my 7 yr-old system for some reason) about a week ago, and this is my first Linux install.  My initial video situation sucked: I had choice of four resolutions, only two of which worked without cutting off whole sides of my display: 800 x 600 and 640 x 480.  At 800 x 600 the size of text and icons was so large that it was impossible to read/access certain parts of different windows.

Once I installed this SiS driver (author claims it comes from an old Chinese distro) things became a bit better:  [http://namakutux.blogspot.nl/2011/11/linux-driver-for-661741760-pciagp-or.html](http://namakutux.blogspot.nl/2011/11/linux-driver-for-661741760-pciagp-or.html)

Even at the same resolution, 800 x 600, I had better access to windows, and once I expanded to the other available resolution (1024 x 768) things are functionally visible.  But when I run video in vls player it freezes (no image) and I have to kill vlc with a -9 switch.  Movie player seems to work, but video is very choppy and sometimes even lags sound.  I also have problems with flash in some cases: can't watch youtube vids, can't see streetview in Google maps--but that might be a separate issue.

I am using a Benq G2220HD monitor, with a native resolution of 1920 x 1080, so 16:9 (I'd love to take advantage of the full width of the monitor, but to be honest I never got Windows XP to do it either...).  Here is the relevant line from lspci:

```
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
```I know my video card sucks, but I only want to be able to watch video on this computer, no gaming.  Is it possible?

---

### Post by DocStrangeLove on 2012-08-26
P.S. My System Settings-->Details still reads "VESA:" and the SiS driver ***did not*** show up in System Settings-->Additional Drivers.  But yet I know something changed after I installed and restarted, because everything looks much better...

---

### Post by mzaam on 2012-08-26
try ```
gstreamer-properties
``` then change video output to X11, change video setting in vlc also,
for resolution u can play with xorg.conf
this may help [http://hellbunker.blogspot.com/2011/03/driver-sis-m671-m672-for-upcoming-natty.html](http://hellbunker.blogspot.com/2011/03/driver-sis-m671-m672-for-upcoming-natty.html)

---

### Post by Bucky Ball on 2012-08-26
*Moved to **Multimedia & Video.***

---

### Post by DocStrangeLove on 2012-08-26
> **mzaam said:**
> try ```
gstreamer-properties
``` then change video output to X11, change video setting in vlc also,
for resolution u can play with xorg.conf
this may help [http://hellbunker.blogspot.com/2011/03/driver-sis-m671-m672-for-upcoming-natty.html](http://hellbunker.blogspot.com/2011/03/driver-sis-m671-m672-for-upcoming-natty.html)

Okay so firstly on the terminal dialog I got a number of errors:
```
(gstreamer-properties:7263): Gtk-WARNING **: Unknown property: GtkDialog.has-separator

(gstreamer-properties:7263): Gtk-WARNING **: Unknown property: GtkDialog.has-separator
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosrc'
```And then when I switched video to X11 I and click "Test" i get the following error message: 
```
gstreamer-properties-Message: Error running pipeline 'X Window System (X11/XShm/Xv)': Could not initialise Xv output [xvimagesink.c(1443): gst_xvimagesink_get_xv_support (): /GstPipeline:pipeline0/GstXvImageSink:xvimagesink1:
No port available]
```

P.S. How do I re-initialize video from the terminal after making changes? (Or is that a stupid question?)

---

### Post by DocStrangeLove on 2012-08-26
P.S. Apparently I don't have a xorg.conf file (nothing turned up on a "find" command with the xorg* file mask).  Do you have a link to a page explaining how to format it?

Sorry, but this thread was bumped from "Absolute Beginner", perhaps unjustly... ;)

---

### Post by mzaam on 2012-09-01
try install gstreamer-plugin-good and gstreamer-plugin-bad. search it it not the exact name,
u can make your own xorg.conf use gedit or other text editor and save it as xorg.conf

u can also try to compile  and use driver provided at that blog

---

