---
title: "where is the 'radeon' driver?"
date: 2007-06-15
forum: Multimedia &amp; Video
---

### Post by gnychis on 2007-06-15
Hey all,

I'm a Gentoo convert and I used to use the 'radeon' driver in X.  For my xorg.conf I had 'radeon' in the driver field.

So, in ubuntu i did apt-get install xserver-xorg-video-ati and it installed the 'ati' driver.  Is this the same thing?  I believe it was the open source version of the driver I was using.

Thanks!
George

---

### Post by Enverex on 2007-06-15
It is. video-ati is basically a metapackage that contains all the open source drivers for ATi cards (rage128, radeon, mach etc).

---

