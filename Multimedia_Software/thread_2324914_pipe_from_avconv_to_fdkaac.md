---
title: "pipe from avconv to fdkaac"
date: 2016-05-17
forum: Multimedia Software
---

### Post by roxas2 on 2016-05-17
need help
/usr/bin/avconv -i "/home/xemnas/Music/1.m4a" -vn -acodec pcm_s16le - |  fdkaac --profile 29 --bitrate-mode 1 -a 1 -o "/home/xemnas/Music/song.m4a" -


the above gives the error
[NULL @ 0x1623a80] Unable to find a suitable output format for 'pipe:'
pipe:: Invalid argument
ERROR: unsupported input file



did i do this wrong????

---

### Post by roxas2 on 2016-05-17
wow... found the answer
again....

avconv -i "/home/xemnas/Music/1.m4a" -vn -strict experimental -acodec pcm_s16le -f wav - |  fdkaac --profile 29 --bitrate-mode 1 -a 1 -o "/home/xemnas/Music/song.m4a" -

i missed the -f wav part

---

### Post by goofprog on 2016-05-19
AAC is always experimental in Linux.  Why is that so?

---

### Post by mc4man on 2016-05-19
> **goofprog said:**
> AAC is always experimental in Linux.  Why is that so?
It _was_ experimental for ffmpeg native aac _encoding_, no longer in more recent versions. As far as what was being done here the option is irrelevant as fdkaac is doing the encoding, not avconv or ffmpeg

(- plus I believe the posted command is missing a - 
this would work here, missing - in red
```
ffmpeg -i 1.m4a -f wav - | fdkaac -p 2 -m 5 -a 1 [COLOR="#FF0000"]-[/COLOR] -o 2.m4a
```

---

