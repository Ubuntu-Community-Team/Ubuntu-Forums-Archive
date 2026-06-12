---
title: "K3b Help plz"
date: 2007-06-29
forum: Multimedia &amp; Video
---

### Post by Darth_Maul on 2007-06-29
When I opened k3b this is what poped up?

DMA disabled on device TSSTcorp - CD/DVDW TS-H652M
With most modern CD/DVD devices enabling DMA highly increases read/write performance. If you experience very low writing speeds this is probably the cause.
Solution: Enable DMA temporarily as root with 'hdparm -d 1 /dev/hda'.

---

### Post by WSmart on 2008-06-25
I just fixed this on my system, same error. 

I had a standard 40 line IDE cable on the optical drive.  I think you generally need an 80 line, DMA cable for that. That fixed the error for me, which is cool because now I'm back up with K3b!  I really like that program.

---

