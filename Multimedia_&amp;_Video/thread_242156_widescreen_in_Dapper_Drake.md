---
title: "widescreen in Dapper Drake"
date: 2006-08-23
forum: Multimedia &amp; Video
---

### Post by MST3Kakalina on 2006-08-23
I've been running Kubuntu without any problems on this laptop so far, save for one minor one.  Native resolution with my monitor is 1280x800, but my max only seems to be 1024x768.  I imagine it's just as simple as changing something in xorg.conf, but what?  Here's the relevant bits:

> Section "Monitor"
  identifier "Generic Monitor"
  vendorname "Plug 'n' Play"
  modelname "Plug 'n' Play"
  modeline "1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  gamma 1.0
EndSection

Section "Screen"
  Identifier "Default Screen"
  Device "Intel Corporation Mobile Integrated Graphics Controller"
  Monitor "Generic Monitor"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    modes "1280x800@60" "640x480@60"
  EndSubSection
EndSection

My video card is an Intel Graphics Media Accelerator 950.

---

### Post by mclaren_fan on 2006-08-23
Installing 915resolution will solve your problem.

---

### Post by MST3Kakalina on 2006-08-23
Thanks! That did the trick.  [this]("http://absolutebeginner.wordpress.com/2006/08/20/absolute-beginner-guide-915resolution/") how-to was very clear and helpful, as well (just for future search references).

---

### Post by splunk on 2006-08-23
Thank you so much for the link to the howto.  Now my 700m is back to normal :)

---

