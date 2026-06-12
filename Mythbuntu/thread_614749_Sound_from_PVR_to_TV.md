---
title: "Sound from PVR to TV"
date: 2007-11-16
forum: Mythbuntu
---

### Post by ljbeng on 2007-11-16
My speaker out from the mother board, VIA M10000, is connected straight to the TV.  I have the volume cranked up inside MythTV but I have to crank the TV volume way up to hear ok.  Has anyone used a simple amplifier external to the motherboard sound card or is there somewhere else I can look (Ubuntu settings?) to get more volume?  Thanks.

---

### Post by OffAxis on 2007-11-16
How is your system sound in general (outside of the mythtv program)?
Does a cd play with normal volume?
you may have the system volume set low. Run
```
alsamixer
```
on the command line and check it out.

---

