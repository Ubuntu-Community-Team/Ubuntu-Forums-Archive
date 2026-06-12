---
title: "is there a bass controlling program for ubuntu"
date: 2007-01-27
forum: Multimedia &amp; Video
---

### Post by robs112 on 2007-01-27
i was wandering if there was a bass equaliser for ubuntu?????
cheers

robin

---

### Post by deadgobby on 2007-01-27
There is XMMS player that has a graphic EQ.

---

### Post by The Union Forever on 2007-01-27
how many EQ bands does that program have?

---

### Post by robs112 on 2007-01-27
im using rythembox

---

### Post by CowzRule on 2007-01-27
> **The Union Forever said:**
> how many EQ bands does that program have?
XMMS has a 10 band EQ, but it only adjusts what it's playing, not the rest of the system. You can adjust your Bass and Treble with Alsamixer. I like it alot better than the default volume control that's on the top panel. To use Alsamixer, open a terminal and type```
alsamixer
```Use the arrow and M keys to adjust the different sliders and the Esc key to exit. Once you have it set where you want, close it, open another terminal and type```
sudo alsactl store 0
```That will keep your setting as default each time you log in.

For even more info about alsa see the following:
[http://www.ubuntuforums.org/showthread.php?t=205449]("http://www.ubuntuforums.org/showthread.php?t=205449")

---

