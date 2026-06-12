---
title: "Fglrx installed - no 1680x1050 option"
date: 2007-04-16
forum: Multimedia &amp; Video
---

### Post by Ichijin on 2007-04-16
so i just finished installing fglrx, im running feisty beta and when i go to admin->screen res i can't pick 1680x1050.  there are only 3 options 640, 800,1024

can anyone help?

---

### Post by Ichijin on 2007-04-16
k i think i got it, i just replaced 1024 with 1680 in xorg.config

---

### Post by garlik42 on 2007-04-16
Something similar happened to me, I added
Modes "1680x1050" to my Display section and it changed my resolution.
I also have Option "UseEdidFreqs" "True" in my Device section.

Good luck.

---

