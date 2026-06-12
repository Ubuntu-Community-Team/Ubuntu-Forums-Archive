---
title: "cropping image in ekiga"
date: 2007-05-14
forum: Multimedia &amp; Video
---

### Post by hardyn on 2007-05-14
with ekiga, i am getting a much smaller field of vision that i do i windows, or even aMSN... any ideas how a wider field can be produced?

feisty, with logitech notebook delux

thanks.

---

### Post by hardyn on 2007-05-14
bump!

---

### Post by hugmenot on 2007-05-16
> **hardyn said:**
> with ekiga, i am getting a much smaller field of vision that i do i windows, or even aMSN... any ideas how a wider field can be produced?

Is it using the gspca driver? Then it&#8217;s the drivers fault. According to Xhaard he advertises QCIF (the resolution) but the camera cannot supply it. So, since JPEG decoding is not allowed in the kernel he cannot resize the video but can only crop.


Here&#8217;s the respective bug report. Apparently it&#8217;s another issue with Logitech cams.
[http://bugzilla.gnome.org/show_bug.cgi?id=331748](http://bugzilla.gnome.org/show_bug.cgi?id=331748)

---

