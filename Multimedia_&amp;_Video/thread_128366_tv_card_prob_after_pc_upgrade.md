---
title: "tv card prob after pc upgrade"
date: 2006-02-11
forum: Multimedia &amp; Video
---

### Post by @jens on 2006-02-11
Hello

just upgraded a pc. Installed is a new ATI radeon card (PCI express slot) and the tv card Pinnacle PCTV (PCI slot). 
dmesg tells me that the Pinnace card is recognized incl correct tuner and so on. Okay the prob is that it seems that the tv programs (eg tvtime, kdetv) try to use the video card instead of the tv card. So when I start eg kdetv the screen gets black and I've to restart the xserver. tvtime pops up and disappears.
Any hints?

Thank's very much!
Jens

---

### Post by @jens on 2006-02-11
Hello again

here is the error message from tvtime. So I'm pretty sure the program tries to use the video card and *not* the tv card. What should I do? As I wrote the tv card is perfectly recognized. Thank's for any help!
Regards
Jens 


$ tvtime
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/username/.tvtime/tvtime.xml
xvoutput: No XVIDEO port found which supports YUY2 images.

*** tvtime requires hardware YUY2 overlay support from your video card
*** driver. If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: [http://gatos.souceforge.net/](http://gatos.souceforge.net/)
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces.

---

### Post by @jens on 2006-02-12
I had to add 
Option "VideoOverlay" "on" to the Section device in xorg.conf
tvtime is working fine now. However, it seems that the unbuntu version of KDETV is buggy.
$ kdetv
the screen is black and I have to restart the xserver.

regards
Jens

---

### Post by xgj on 2006-02-12
I  have had the same problem

i will try to do it

---

### Post by xgj on 2006-02-12
Thank you!

The problem is solved!

---

