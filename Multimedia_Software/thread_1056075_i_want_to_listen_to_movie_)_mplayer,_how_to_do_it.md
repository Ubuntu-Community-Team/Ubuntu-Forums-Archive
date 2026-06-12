---
title: "i want to listen to movie :) mplayer, how to do it?"
date: 2009-01-31
forum: Multimedia Software
---

### Post by mag_dex on 2009-01-31
Hi,

I have a weird question. When I'm doing sth I like listening the movies like sitcoms (yes, listen, I can't watch). 
It also can be really funny ;)
I've been trying to find some way to just play sound of movie. If I just play the movie I can listen of course, but I have open a new window (I play a movie from console) and I think I waste a bit of power of my weak laptop.

Is there any option in mplayer to turn off the window with video?

:)

---

### Post by Martje_001 on 2009-01-31
For mplayer I don't know, but for VLC it is:
```
Video --> Source (Translated it, can be wrong) --> Deactivate
```

---

### Post by jerome1232 on 2009-01-31
I believe it's

```
mplayer -vo null /path/to/video
```

also
```
mplayer -novideo /path/to/video
```

---

### Post by mag_dex on 2009-02-01
mplayer -novideo /path/to/video 
works perfectly!

Thanks a lot!

---

