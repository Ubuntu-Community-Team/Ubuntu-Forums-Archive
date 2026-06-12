---
title: "No sound in Istanbul-generated screencasts"
date: 2007-03-29
forum: Multimedia &amp; Video
---

### Post by elreteipos on 2007-03-29
I made a screencast with Istanbul, but it didn't record the sound although I checked 'Record sound'. Is there a way to fix this?

---

### Post by adastra23 on 2007-04-07
I am also having the same issue with istanbul

HP Compaq Presario Media Center Sr1920nx PC

Processor - AMD Athlon 64 3500+ processor with Enhanced Virus Protection
Memory - 512MB DDR PC3200 memory
Graphics card - Integrated Nvidia GeForce 6150LE Graphics with up to 256MB shared video memory.
integrated audio made by Realtek.

I found istanbul to work fine except for this one issue (no sound)

Also, anybody have suggestions on how to convert the .ogg movies to other formats?
Thanks

---

### Post by elreteipos on 2007-04-08
> **adastra23 said:**
> Also, anybody have suggestions on how to convert the .ogg movies to other formats?
Perhaps mencoder can do it (Ubuntu package name: mencoder). I think its syntax is something like> mencoder inputfile.ogg -o outputfile.mpgI'm not sure, nor have I tested this. Read the manpage of mencoder for more information.

---

