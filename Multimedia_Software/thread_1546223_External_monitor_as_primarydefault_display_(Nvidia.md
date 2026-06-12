---
title: "External monitor as primary/default display (Nvidia)"
date: 2010-08-05
forum: Multimedia Software
---

### Post by cpudney on 2010-08-05
G'day,

Hopefully, this will save others a bit of time.

I recently installed [Lucid Lynx on my Dell Inspiron 9400]("http://ubuntu-linux-dell-inspiron-9400.blogspot.com/2010/08/external-monitor-as-primarydefault.html").  One niggling annoyance was that the Dell's LCD screen was the primary display, whereas I wanted my external monitor (BenQ T2200D via DVI) to be the primary display.

Ultimately, the solution was simple:
[LIST=1]
[*]run the *NVidia X Server Settings tool* ([FONT="Courier New"]gksudo nvidia-settings[/FONT])
[*]in the *X Server Display Configuration* I made sure the Dell's display (Seiko) was **disabled**
[*]when saving to the X Configuration file, i.e. /etc/X11/xorg.conf, I chose **not** to *merge with existing file*
[*]restart X
[/LIST]

---

