---
title: "How to play subtitle in mplayer"
date: 2007-02-23
forum: Multimedia &amp; Video
---

### Post by kanha on 2007-02-23
How to play subtitle (.srt,.txt) in mplayer ? I know that it can play but can't find option. :(
please help

between can we play subtitle in totem

---

### Post by CyberAngel on 2007-02-24
if the subtitles filename is the same as movie filename (e.g. movie.avi and sub file movie.srt) then at least for me it is loading subs automatically.
Else you can tell mplayer to load subs with option "-sub"

```
mplayer -sub movie.srt movie.avi
```

---

