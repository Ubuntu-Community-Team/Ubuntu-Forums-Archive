---
title: "Console mode text is green!"
date: 2010-06-14
forum: Multimedia Software
---

### Post by BillRebey on 2010-06-14
I'm using 10.04 Server in console/text mode (no GUI).  I have Grub and Ubuntu both loading at 1600x1200x16.  I'm using, in grub.cfg:
```
set gfxmode=1600x1200x16
set gfxpayload=1600x1200x16
insmod gfxterm
insmod vbe
```
This works for getting the thing into 1600x1200, and the colors in Grub2 are correct, but once Ubuntu starts, everything is "mostly" green.  By "mostly", I mean that colors - such as those in my prompt string - are still there - blue, red, etc. - they just look like they're behind a dark green lens.
Any ideas what's going on here, and how to correct it?

---

