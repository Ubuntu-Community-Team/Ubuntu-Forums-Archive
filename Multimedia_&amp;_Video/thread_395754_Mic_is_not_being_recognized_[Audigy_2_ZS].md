---
title: "Mic is not being recognized [Audigy 2 ZS]"
date: 2007-03-28
forum: Multimedia &amp; Video
---

### Post by xstaticxgpx on 2007-03-28
There seems to be a issue with ubuntu regonizing my mic that's connected to my soundcard (Audigy 2 ZS), I'm trying to get it to work with wine/ventrilo for gaming, but not even the Sound Recorder App in "Menu>Sound & Video" recognizes I have a mic. This is getting pretty frustrating since this has worked for me on a previous installation of ubuntu (don't remember if it was 6.06 or 6.10, tho)

---

### Post by xstaticxgpx on 2007-03-28
uh... bump

---

### Post by xstaticxgpx on 2007-03-29
nobody? any ideas?

---

### Post by xstaticxgpx on 2007-03-30
well these forums got really helpful...:???:

---

### Post by fluoblack on 2007-04-20
I had the same problem with my Audigy 2. I just found the solution, I guess it should work on yours.

it seems the alsamixer's GUI doesn't work quiet good on the mic, so start alsamixer **in the console**, find the mic stuff, increase the volume and thats it! 

Well at least it worked for me ;)

---

