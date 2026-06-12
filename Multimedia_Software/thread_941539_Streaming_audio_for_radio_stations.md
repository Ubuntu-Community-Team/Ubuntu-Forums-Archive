---
title: "Streaming audio for radio stations"
date: 2008-10-08
forum: Multimedia Software
---

### Post by lanier_t on 2008-10-08
I am trying to setup my Dad using Ubuntu 8.04 (tired of him getting virus) and the one thing I cannot get to work is the streaming audio for his favorite radio station.

Here is the link

[http://www.streamaudio.com/stations/player/pages/newplayer/index_win.asp?Owner=&public=&headertext=&Station=KGSR_FM&Mac=Yes&OptIn=No&Streamtype=&filename](http://www.streamaudio.com/stations/player/pages/newplayer/index_win.asp?Owner=&public=&headertext=&Station=KGSR_FM&Mac=Yes&OptIn=No&Streamtype=&filename)

I have looked around and nothing seems to work for this particular link (other than Windows)  Can someone try this link and see if it works for their setup and share it with me.

---

### Post by kostkon on 2008-10-08
The page did not load well, it was a little messy. I may have pressed something, I don't know, but after 1 min. the stream started playing. I am using *totem-xine*, the *totem-mozilla* browser plugin, of course, and the *w32codecs* windows codecs from the [*Medibuntu*]("http://medibuntu.org/") repository.

I think it is a *Windows Media* audio stream.

Thus, you could, first of all, install the *Totem* *Firefox* plugin (the package is called *totem-mozilla*), if you don't have it already. Then, add the [*Medibuntu*]("http://medibuntu.org/") repository (instructions on how to do it [are on its site]("http://help.ubuntu.com/community/Medibuntu")) and install the Windows codecs package (it is called *w32codecs*). Finally, make sure that the *gstreamer0.10-pitfdll* package is installed in your system.

(you can install the above packages using *Synaptic*)

After doing the above, visit the page again and see if the stream will play.

---

### Post by wolfen69 on 2008-10-08
the website looked all messed up. however, the streaming audio works for me. totem-mozilla is installed by default. but i strongly recommend uninstalling it in favor of mozilla-mplayer. this is only my preference, but it works very well. and yes, the medibuntu repos won't hurt.

---

