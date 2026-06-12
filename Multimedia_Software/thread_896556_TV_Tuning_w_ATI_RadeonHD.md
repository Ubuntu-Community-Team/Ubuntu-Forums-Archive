---
title: "TV Tuning w/ ATI RadeonHD"
date: 2008-08-21
forum: Multimedia Software
---

### Post by bieber on 2008-08-21
I've currently got a Hauppage TV tuner card and a RadeonHD 2400 Pro in an 8.04.1 64-bit box.  The tuner is installed correctly, but when I run TV-Time, it tells me 
> 
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
I/O warning : failed to load external entity "/home/bieber/.tvtime/tvtime.xml"
I/O error : Permission denied
I/O error : Permission denied
Cannot change owner of /home/bieber/.tvtime/tvtime.xml: Permission denied.
xvoutput: No XVIDEO port found which supports YUY2 images.

*** tvtime requires hardware YUY2 overlay support from your video card
*** driver.  If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: [http://gatos.souceforge.net/](http://gatos.souceforge.net/)
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces.

I know installing ATI's proprietary driver would fix that, but I'm not willing to do so: rather, is there a solution using only free software?  Could the RadeonHD driver handle it?  I've installed the driver in Synaptic, but I can't figure out how to actually use it (do I need to edit xorg.conf?)  Any help is greatly appreciated.

---

