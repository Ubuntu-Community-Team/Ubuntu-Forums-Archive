---
title: "Dell OptiPlex GX1P"
date: 2005-12-09
forum: Multimedia &amp; Video
---

### Post by Hootman on 2005-12-09
Got everything working but sound. Any help as what to do.

---

### Post by efren_reyes on 2006-03-23
Elevate to root (sudo su)

open /etc/modules with editor of choice

uncomment (add #) to the begining of the line beginning with "snd-4256"  (maybe snd-4236, don't remember).  

Reboot.

Should work, common problem with 500/550 dell gx1s.

---

