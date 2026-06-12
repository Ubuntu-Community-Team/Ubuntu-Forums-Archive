---
title: "Some colors in firefox coming out inverted"
date: 2011-05-29
forum: Multimedia Software
---

### Post by dannyboytward on 2011-05-29
After upgrading to Natty/Unitiy I was having problems with very slow and choppy window motion.  I tried reinstalling fglrx, and now some of the colors in firefox are coming out inverted (e.g. yellow -> purple) or perhaps just scrambled in some other way (see attached screenshot).  There are no other issues I've seen other than some colors in firefox.  Most colors look okay.  

I downloaded chromium and there are no problems with colors there.  I've also upgraded to the latest fglrx drivers from the ATI website and nothing changed.  I also uninstalled and reinstalled firefox and still the colors are coming out strangely.

Some info.  I have an HP Pavilion tx2500ca, with ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics].

Any help or suggestions would be very much appreciated.  This seems very strange to me.

---

### Post by lovinglinux on 2011-05-30
See [http://www.webgapps.org/tutorials/firefox/troubleshooting/rendering-issues-and-solutions](http://www.webgapps.org/tutorials/firefox/troubleshooting/rendering-issues-and-solutions)

---

### Post by dannyboytward on 2011-05-30
Thank you.  I typed about:config in the address bar, and changed the property gfx.color_management.mode from 2 to 0.  This worked and the colors are all normal again.

---

### Post by lovinglinux on 2011-05-30
> **dannyboytward said:**
> Thank you.  I typed about:config in the address bar, and changed the property gfx.color_management.mode from 2 to 0.  This worked and the colors are all normal again.

You are welcome.

---

