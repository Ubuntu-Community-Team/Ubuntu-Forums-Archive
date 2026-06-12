---
title: "Nvidia Nforce AD1986A no headphone jack output [SOLUTION]"
date: 2007-10-03
forum: Multimedia &amp; Video
---

### Post by jpross81 on 2007-10-03
Every time I try to get my sound working I have to go through the same thing and for some reason I can never get my **headphone jack working** right away.  After I browse post after post and try all sorts of different "solutions" I finally find one that works.  Because of this post, next time I will know exactly what to do to fix it and hopefully this will help you guys too.  

follow the directions at this page...
[https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

And if you have my AD1986A device make sure you add the following line to the end of /etc/modprobe.d/alsa-base
```
options snd-hda-intel model=3stack

```

and **make sure you spell it right!**


Very simple!  don't let a typo like... options snd-had-intel model=3stack 
keep your headphones from working like it did to me!

---

