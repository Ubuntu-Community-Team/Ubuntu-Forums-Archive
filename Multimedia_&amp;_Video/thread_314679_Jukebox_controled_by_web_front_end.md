---
title: "Jukebox controled by web front end"
date: 2006-12-07
forum: Multimedia &amp; Video
---

### Post by pietro_spina on 2006-12-07
I'd like to set up an old computer to play our library of music through the stereo, however I want to control it from any(mac/win/linux) computer on the network...

Maybe a web front end for gstreamer?...  can anyone point me in the right direction for something like that?

thanks-
-pietro

---

### Post by K.Mandla on 2006-12-07
It was my understanding that [mpd]("http://packages.ubuntu.com/edgy/sound/mpd") was meant to run with some sort of server-client arrangement. I don't know of any Web interfaces that are in the repos, but there are a few options [here]("http://musicpd.org/clients.shtml"). They shouldn't be too hard to set up.

---

### Post by pietro_spina on 2006-12-08
from what I can tell, it looks like these are all about streaming the music back through the internet. I just want it to play through the audio output... just to control from the web...

---

### Post by pietro_spina on 2006-12-09
thanks K.Mandla....

I looked closer at the config file for [Ampache]("http://www.ampache.org/") (one of the web clients for mpd) and it looks like this does exactly what I want *and* allows for streaming as well. Almost all of its features (streaming/dwnloading...) can be disabled if you are so inclined. Now I'll just have to wait for the office to upgrade a couple of workstations and let me get my hands on the cast-off parts...

thanks.
-pietro

---

