---
title: "External monitor as default/primary display (Nvidia)"
date: 2010-08-05
forum: Multimedia Software
---

### Post by cpudney on 2010-08-05
G'day,

Hopefully, this will save others some time.

I recently [installed Lucid Lynx on my Dell Inspiron 9400]("http://ubuntu-linux-dell-inspiron-9400.blogspot.com/2010/08/installing-lucid-lynx-1004-on-dell.html").  One niggling annoyance was that the Dell's LCD screen was the primary display, whereas I wanted my external monitor (BenQ T2200D via DVI) to be the primary display.

Ultimately, the solution was simple:

   1. run the *NVidia X Server Settings* tool ([FONT="Courier New"]gksudo nvidia-settings[/FONT])
   2. in the *X Server Display Configuration* I made sure the Dell's display (Seiko) was **disabled**
   3. when saving to the X Configuration file, i.e. [FONT="Courier New"]/etc/X11/xorg.conf[/FONT], I chose **not** to *merge with existing file*
   4. restart X

HTH,
Chris.

---

