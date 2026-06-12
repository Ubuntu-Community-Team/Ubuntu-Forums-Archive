---
title: "clean removal of graphics card drivers"
date: 2006-06-22
forum: Multimedia &amp; Video
---

### Post by xolot1 on 2006-06-22
i have a ati xpress 200m graphics card on my laptop, and im looking to get it working.  ive tried a number of different approaches, but still havent got it working.  im slighty afraid that previous attempts are botching my newer attempts.  how should i go about removing all references to graphics cards stuff each session.

i figure this would include remodifying xorg.conf, and some removal of packages, fglrx, etc.  but which ones, and how?

thanks

---

### Post by GuitarHero on 2006-06-22
try

sudo dpkg-reconfigure xserver-xorg

---

### Post by xolot1 on 2006-06-22
thank you.

i was wondering what packages, files, etc might have been modified in trying to get fglrx/ati drivers to work. then how i might go about reverting them.

thanks for the tip on xorg.

---

