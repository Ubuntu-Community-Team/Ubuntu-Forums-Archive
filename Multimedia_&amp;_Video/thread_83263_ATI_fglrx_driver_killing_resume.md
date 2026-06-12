---
title: "ATI fglrx driver killing resume"
date: 2005-10-28
forum: Multimedia &amp; Video
---

### Post by wakeboarder on 2005-10-28
Suspend/resume was working fine then I "upgraded" the driver to ATI fglrx.

Now it freezes when trying to resume.

If I change  the driver back to "ati" in xorg.conf it works again.

Any hints ? :confused:

---

### Post by soonindallas on 2005-10-28
I live with a similar issue running 5.10 on an Acer 1683: hibernate/resume worked fine with the stock drivers.  using the fglrx drivers (I installed ATI Proprietary Linux Drivers 8.18.6) causes resume from hibernation to fail -- reload seems to work ok but screen shows a bunch of c**p and computer hangs.

it was the same with Hoary.

---

### Post by wakeboarder on 2005-12-02
I got the answer in another forum that the fglrx driver doesn't support suspend/resume!

---

