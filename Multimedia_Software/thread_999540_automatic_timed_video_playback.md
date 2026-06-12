---
title: "automatic timed video playback?"
date: 2008-12-02
forum: Multimedia Software
---

### Post by elwillow on 2008-12-02
Good evening,

background:
I'm looking for a completely automated solution to show video at a convention.

question:
Is there a way to have videos played full screen (yes, mplayer -fs) WITHOUT the need for a X server? like a direct "mplayer -> video card" link?

my current idea is to use crontab and set up the video schedule the day before and have it run on its own. the next day. Before I go into a extended testing period I want to probe around if someone knows/thinks/learned if this is possible...

So, what is the best solution for me?

I'm ready to hear all options (and no, a slave will not do, although it would be easy to get)

---

### Post by jpkotta on 2008-12-03
This might be helpful, at least if you are looking at using cron.

[http://ubuntuforums.org/showthread.php?t=948111](http://ubuntuforums.org/showthread.php?t=948111)

Of course, you'll need an xserver to be running already.  There are ways of setting up an automatic log in.

Maybe you could just use something like
```
startx /usr/bin/mplayer -fs video.mkv
```
from cron.

---

