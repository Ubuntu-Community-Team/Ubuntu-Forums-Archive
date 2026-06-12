---
title: "icedax not in Applications menu"
date: 2012-01-09
forum: Multimedia Software
---

### Post by briar rabbit on 2012-01-09
Hi
I downloaded icedax into my lenovo T61 with 10.04 ubuntu.  icedax does not showup in the Applications menu.  It does showup in /usr/bin but will not open. 

help

thank you

---

### Post by mc4man on 2012-01-09
That's because icedax is not a gui application, it's a command line audio extractor, Debian's replacement for cdda2wav | cdparanoia

Run 
man icedax or icedax -h
and or install cdrkit-doc, browse to /usr/share/doc/cdrkit-doc/icedax, there are some files you can read.

Long run you'd probably be better off finding a ripping app you like & using it, there are quite a few available

---

### Post by briar rabbit on 2012-01-09
OK,

I have cdrkit-doc  and found /usr/share/doc/cdrkit-doc/icedax.
That may explain why my search for icedax info earlier did not come back with anything.

Thanks mac4man for taking the time to help a newbie.
And, I will be looking over the ripping application choices.

---

