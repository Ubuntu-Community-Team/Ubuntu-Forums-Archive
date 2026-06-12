---
title: "Fullscreen video playback doesn't work in MPlayer"
date: 2010-01-10
forum: Multimedia Software
---

### Post by zoubidoo on 2010-01-10
Fullscreen video playback doesn't work in MPlayer.  I don't know if or where this should be reported.

mplayer        2:1.0~rc3+svn2
Ubuntu 9.10 on i386

Solution:  
```
mplayer -vo gl filename
```


Thanks to:
[http://www.linuxforums.org/forum/slackware-linux-help/89813-mplayer-fullscreen-problem.html](http://www.linuxforums.org/forum/slackware-linux-help/89813-mplayer-fullscreen-problem.html)

Just thought this might help someone in the same position.

Z.

---

### Post by andrew.46 on 2010-01-10
Hi zoubidoo,

Perhaps your default -vo is something like x11? The following should also work:

```
mplayer -vo x11 -zoom -fs ***[COLOR="Red"]filename[/COLOR]***
```

If you omit the '-fs' MPlayer will still be able to go to full screen with the default 'f' key.

Andrew

---

### Post by zoubidoo on 2010-01-11
Thanks for the suggestion Andrew, but -vo x11 doesn't work.  Even though mplayer takes over the whole screen, the image remains at the original size and the surrounding space is black.

---

