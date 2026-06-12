---
title: "Ripping audio from ISO of 5.1 audio DVD"
date: 2012-03-24
forum: Multimedia Software
---

### Post by ZICODIAN on 2012-03-24
Hi *

Would you happen to know how one might attempt to rip audio from the ISO image of a 5.1 audio DVD? What I would like to do is convert the tracks of the ISO image to FLAC files. Is there a program you could recommend to do this?

Thanks!

---

### Post by shantiq on 2012-03-24
well zicodian   first unpack it   right click on iso and choose extract here



you now have some VOB files inside VIDEO folder



use ffmpeg to turn them into flac   open terminal   cd to the folder where VOB s are   enter



> for f in *.VOB ; do ffmpeg -i "$f" "${f%.VOB}.flac"; done


then use audacity   to split/trim your flac tracks if you are dealing with a music video



is the way i would proceed:KS   hope this makes sense to you

---

### Post by ZICODIAN on 2012-06-20
> **shantiq said:**
> well zicodian   first unpack it   right click on iso and choose extract here



you now have some VOB files inside VIDEO folder



use ffmpeg to turn them into flac   open terminal   cd to the folder where VOB s are   enter






then use audacity   to split/trim your flac tracks if you are dealing with a music video



is the way i would proceed:KS   hope this makes sense to you
Thanks muchly for your assistance. That worked nicely and was very clear.

---

