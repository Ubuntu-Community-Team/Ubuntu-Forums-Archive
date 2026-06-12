---
title: "Real Player &amp; BBC clips"
date: 2006-11-07
forum: Multimedia &amp; Video
---

### Post by Tantalus90 on 2006-11-07
Edgy and realplayer 10 with firefox plugin 

can not seem to open any of the news clips available from the beeb 

[http://news.bbc.co.uk/](http://news.bbc.co.uk/)

has somethign changed with either realplayer or bbc ?

they load (sort of) as windows media files but the real feeds tend to be much faster and reliable with less drop outs and hangs mid clip so i wanted to use realplayer 

any advice would be welcome :)

---

### Post by Fell on 2006-11-07
I've also had problems with this. My solution is not the most elegant but works for me. Maybe someone else can post a better solution.

I found that when I tried to play the file it was the totem plugin that Firefox was trying to use. Since I use the mplayer plugin anyway, I just removed the totem one.

sudo aptitude remove totem-mozilla

After that was removed I found that Firefox tried to use the mplayer plugin for Realplayer files. To get it to play using the Realplayer plugin I deleted the following two files from /usr/lib/mozilla-firefox/plugins/

mplayerplug-in-rm.so
mplayerplug-in-rm.xpt

Hope this helps.

---

### Post by Fell on 2006-11-07
I've just found this thread...

[http://www.ubuntuforums.org/showthread.php?t=293468&highlight=realplayer]("http://www.ubuntuforums.org/showthread.php?t=293468&highlight=realplayer")

The 5th post seems to be a much simpler solution that the one I posted above.

---

### Post by Tantalus90 on 2006-11-07
> **Fell said:**
> I've just found this thread...

[http://www.ubuntuforums.org/showthread.php?t=293468&highlight=realplayer]("http://www.ubuntuforums.org/showthread.php?t=293468&highlight=realplayer")

The 5th post seems to be a much simpler solution that the one I posted above.
 thanks :) 

linky [http://www.ubuntuforums.org/showpost.php?p=1718816&postcount=5](http://www.ubuntuforums.org/showpost.php?p=1718816&postcount=5)

realplayer still not picking them up though, but uninstalling mplayer and plugin seemed to help

---

### Post by ron999 on 2007-02-22
> **Fell said:**
> I've just found this thread...

[http://www.ubuntuforums.org/showthread.php?t=293468&highlight=realplayer]("http://www.ubuntuforums.org/showthread.php?t=293468&highlight=realplayer")

The 5th post seems to be a much simpler solution that the one I posted above.

Thanks Fell, that thread solved my problem too.  :D :D

---

