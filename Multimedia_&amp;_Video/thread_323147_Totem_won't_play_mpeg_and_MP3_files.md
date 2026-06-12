---
title: "Totem won't play mpeg and MP3 files"
date: 2006-12-21
forum: Multimedia &amp; Video
---

### Post by rajat200 on 2006-12-21
Hi,
I have just finished mounting windows partition and when I try to play MP3 and MPEG files it opens Totem Player. I get an error message " Totem could not play 'file:///media/sda7/Movies/million dollar baby dvd rip.mpg'."

What can I do to resolve this issue?

Any help is appreciated....

Regards
Rajat Bhargava

---

### Post by s6dalane on 2006-12-21
You should follow [this]("https://help.ubuntu.com/community/RestrictedFormats") guide and install the necessary codecs.

---

### Post by rajat200 on 2006-12-21
Thanks a lot friend...

---

### Post by bigken on 2006-12-21
you could use [automatix]("http://www.getautomatix.com/wiki/index.php?title=Installation") this will solve all your codec problems ;)

---

### Post by Tanker Bob on 2006-12-22
> **bigken said:**
> you could use [automatix]("http://www.getautomatix.com/wiki/index.php?title=Installation") this will solve all your codec problems ;)

Great point-out!  I'm brand new to Ubuntu and Linux, and I had the same problem.  Xine worked fine, but Totem always complained.  Automatix worked perfectly and solved the problem.  Thanks!

---

### Post by jcroot on 2006-12-22
I just installed Automatix but I don't know what to do next to play MP3 and MPG videos, I just want to be able to play MP3 music and MPG videos, avi videos and windows media player video.

Can somebody please give me a hand?

I also went to this site and follow these instructions:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

But I still not able to play mp3 audio and mpg videos.

---

### Post by jocheem67 on 2006-12-23
You should install totem-xine, w32codecs, libxine-extracodecs and be able to play avi, mp3 and wmv. Especially the extracodecs are quite important. They should be in multiverse, otherwise do a google on them. If you don't know how to add extra repositories search this forum. There  are several threads around.

---

