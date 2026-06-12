---
title: "can't export to mp3 using libmp3lame.so.0.0.0"
date: 2007-03-19
forum: Multimedia &amp; Video
---

### Post by grahamdoel on 2007-03-19
I have been trying to export to mp3 file format in Audacity (and others, but Audacity mainly.

I can export to ogg happily, unfortunately the majority of my audience don't have the ability/capability/knowledge, so I do need mp3.

I have a sym link from libmp3lame.so and libmp3lame.so.0 to libmp3lame.so.0.0.0 and when I export it generates a file just under 1 Mb that plays a split second of nothing.

Could any one point me in the right direction?  Thanks

---

### Post by ubromtoo on 2007-04-03
Same problem here; what I do for a temporay solution is to export the file

from Audacity, then load it into a different audio editor called "mhWaveEdit"

and, without doing any editing, export it as an mp3 file.

    A bit laborious, but it works!

---

### Post by armalite on 2007-04-03
Same for me in Feisty. Package liblame-dev provides libmp3lame.so (so no need of symlinks), but the end result is the same as above, file too small to be playable.

A workaround is to encode in FLAC and then use SoundConverter to encode mp3.

---

### Post by ubromtoo on 2007-04-07
Tried SoundConvertor but it wouldn't work for me.

 then tried the similarly-named SoundKonverter and it will do the job.

---

