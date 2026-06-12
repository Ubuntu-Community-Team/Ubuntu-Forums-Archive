---
title: "[SOLVED] Videoplayer that can show subtitles"
date: 2008-08-06
forum: Multimedia Software
---

### Post by silvanus2005 on 2008-08-06
Can anyone tell me if I can find a videoplayer that can show subtitles in Ubuntu? I use BSplayer in XP, is there any other application similar to BS player in Ubunu?

---

### Post by aeiah on 2008-08-06
mplayer, xine and vlc will show subtitles. since most players are based on either mplayer or xine, you'll find that all of them will display subs. of course, there are some quirks with certain subs but i never have problems. i use gmplayer. a lot of people prefer smplayer though. both are based on mplayer, obviously.

---

### Post by silvanus2005 on 2008-08-08
I tried all three, but only VLC shows subtitles. It not show them all, only 1/3 of them :( Any other suggestion?

---

### Post by Archmage on 2008-08-08
For me mplayer is showing ALL the subtitles. You just need to make sure that movie and sub have the same filename. E.g.

Steal_this_movie.mov
Steal_this_movie.srt

---

### Post by kpkeerthi on 2008-08-08
Just drag and drop the srt file onto the mplayer window playing the video. Automagic!

---

### Post by silvanus2005 on 2008-08-10
MPlayer works ok. It has one problem, though - the font of the subtitles is very big, it takes half of my screen. Any solution to change the size of the font?

---

### Post by rvm4000 on 2008-08-10
```
man mplayer
```

look for -subfont-text-scale, -subfont-autoscale and -a s s-font-scale

---

### Post by kpkeerthi on 2008-08-11
There was a post in this forum on 'the ultimate mplayer config file'. A quick search should get you that :)

---

