---
title: "OGG plays in MMMX but not in Rhythmbox?"
date: 2006-08-31
forum: Multimedia &amp; Video
---

### Post by Garyu on 2006-08-31
Hey,

I just ripped some CD's with Sound Juicer to OGG files, but I can't play them in Rhythmbox! They play fine in Mplayer, VLC, MMMX but not in Rhythmbox which is my player of choice. Anyone know how to fix this? 

I don't get an error, only a red-white sign next to the ogg song. I searched synaptic for all ogg and ogm and vorbis stuff, but I got most of it installed already, so I think it is a configuration issue, but I don't know what to configure or how?

---

### Post by pertti on 2006-08-31
There is nothing to configure in Rhythmbox itself. For playing ogg vorbis files all you need is the gstreamer0.10-plugins-good package, which should be installed by default. Check if you have it installed, and try to play the files with Totem, which also uses GStreamer for playing audio (and video) files.

If Totem works but Rhythmbox doesn't, then it's Rhythmbox's fault (really strange). In this case, maybe you could give Rhythmbox 0.9.5 a try, using [the .deb package]("http://www.mikesplanet.net/?p=37") on [this thread]("http://www.ubuntuforums.org/showthread.php?t=200762"). I've been using it for a couple of months and it's been working flawlessly so far.

If Totem also fails to play the file, it's GStreamers fault. Maybe you could try uninstalling gstreamer and the installing it again...

Hope this helps!

---

### Post by Garyu on 2006-08-31
uhm, I tried it in Totem and it worked. Then I went back to Rhythmbox and suddenly it worked there too. I messed around with sound things here and there before, so maybe I managed to do something right, or maybe it was just a temporary thing (if that is even possible). Anyways, it's working now, so I'm happy. :D

---

