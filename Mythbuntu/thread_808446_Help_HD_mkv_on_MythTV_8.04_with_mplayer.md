---
title: "Help HD mkv on MythTV 8.04 with mplayer"
date: 2008-05-26
forum: Mythbuntu
---

### Post by omnibrown on 2008-05-26
MythTV works great except for playing my HD mkv x.264 files. My set up:

Mythbuntu 8.04 with the current nvidia driver, 169.12

AMD Athlon 64 X2 6400+ Windsor 3.2GHz Socket AM2 125W Dual-Core
2 GB RAM
nVidia GeForce 7050 PV

I've tried mplayer with various options and niceness, best luck is having a movie play for like 5 mins, then the screen freezes

For example:
mplayer -benchmark -ac hwdts -vfm ffmpeg -lavdopts fast=1:skiploopfilter=all:threads=8

I've tried to increase the niceness too. No luck.

Did some searching but never found a complete answer. Also my mtrr isn't set for the video card. I tried to added it:

echo "base=0xe0000000 size=0x10000000 type=write-combining" > /proc/mtrr 

Didn't make a difference.

---

### Post by omnibrown on 2008-05-28
After a bit more searching I found the best options to use in the MythTV Wiki.  [http://www.mythtv.org/wiki/index.php/HD_Playback_Reports](http://www.mythtv.org/wiki/index.php/HD_Playback_Reports)

```
mplayer -fs -zoom -quiet -vo xv -monitoraspect 16:9 -lavdopts threads=2:fast:skiploopfilter=all -sws 0
```

Played a 13 GB 1080p mkv :)

The system complained that it was too slow after the movie ended, but it played and the system did not hang.

---

