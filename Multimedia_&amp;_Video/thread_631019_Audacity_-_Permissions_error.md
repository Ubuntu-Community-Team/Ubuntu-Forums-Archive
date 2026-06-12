---
title: "Audacity - Permissions error"
date: 2007-12-04
forum: Multimedia &amp; Video
---

### Post by NJC on 2007-12-04
I am having (what I think) is Write errors in Audacity. Other programs (Thunderbird, OpenOffice) can read/write to this disk, but with Audacity I get the following error. Any ideas? It's a Win drive drive with HEAPS of space. 

Mounted via fstab:```
UUID=1610-375D  /media/windows   vfat   user,fmask=0111,dmask=0000   0   0 
```

---

### Post by Prospero2006 on 2007-12-04
I would suggest saving to a different directory and manually copying the information to your windows partition via sudo.

Maybe if you started audacity with the sudo command?


Pros

---

### Post by NJC on 2007-12-04
I was scouring the Audacity forums and it's possible that writing and storing temp files to different drives could be problematic (which is what I'm doing). I'll try to consolidate it to one drive and see if it makes a difference.

---

