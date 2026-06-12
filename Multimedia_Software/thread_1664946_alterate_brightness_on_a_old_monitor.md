---
title: "alterate brightness on a old monitor"
date: 2011-01-11
forum: Multimedia Software
---

### Post by magowiz82 on 2011-01-11
Hi,
since I have a very old monitor that shows too dark colours I would like to increase the brightness via software, in another distro I used gxvattr but in ubuntu doesn't work, I also tried gdcccontrol but my monitor isn't supported.
What should I try ?

---

### Post by magowiz82 on 2011-01-12
bump

---

### Post by luismgl on 2011-03-04
bump on this, have the same problem, running ubuntu desktop 10.10
edit: dunno if it matters but the monitor in question is a philips 105e11

---

### Post by magowiz82 on 2011-03-04
Please give a try to xgamma , I solved with it. To make changes permanent add option Gamma to /etc/X11/xorg.conf in Monitor section.

---

