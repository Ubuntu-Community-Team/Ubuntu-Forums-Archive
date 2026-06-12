---
title: "mplayer cache option greatly reduces performance"
date: 2010-03-11
forum: Multimedia Software
---

### Post by leniviy on 2010-03-11
Hi. I needed a larger cache because I have some videos stored on another samba server and it's laggy. 
I set options: cache=20000, cache-min=10 , and that helped to play those videos smoothly, but that caused all 1280x720 mp4 files stored on my local drive to lag and A/V desync with mplayer message: 
**** Your system is too SLOW to play this!  ****

I tried cache values from 1000 to 80000, and they lag in any case. But without the option "cache" these videos play well.
Now I commented "cache" in config.
```
[default]
#cache=65536
#cache-min=10
ao=alsa
softvol=yes
subcp=enca:ru:cp1251
af=pan=2:1:0:0:1:1:0:0:1:0.5:0.5:1:1
&#1072;ss=yes
```In short, even with -nocache they play faster than with any cache. Unoptimized? Broken?
MPlayer SVN-r30526-4.4.3

---

