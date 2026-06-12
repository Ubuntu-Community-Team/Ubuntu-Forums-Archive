---
title: "AVIDEMUX - PAL output option rather than NTSC"
date: 2007-04-05
forum: Multimedia &amp; Video
---

### Post by Yeuclid on 2007-04-05
I've had to give up on Devede for demuxing AVI files to DVD format due to sound problems so now attempting to use AVIDEMUX and QDVDAUTHOR. A bit long winded, but better than nothing.

My problem is that I can't find an option in AVIDEMUX to produce PAL format output. I appears to always default to NTSC.

What am I missing here, surely it must be possible.

---

### Post by ruibernardo on 2007-04-07
I think this happens because the original file must have a 23,xxx or 29,xxx framerate. It  creates a pal movie if the original was 25 FPS. 

You can apply a filter in Avidemux to change the framerate, and only then create the pal movie.

I think that most dvd players knows how to handle ntsc movies without you even notice.

---

### Post by Yeuclid on 2007-04-07
I've done it with FFMPEG cli. Quite simple, even if not GUI, so I'll leave AVIDEMUX on the shelf for the moment.

I have an old DVD player which is quite fussy about the source material.

---

