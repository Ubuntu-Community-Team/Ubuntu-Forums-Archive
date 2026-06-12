---
title: "[SOLVED] best player for radio stream mp3.m3u files?"
date: 2008-08-24
forum: Multimedia Software
---

### Post by amplexus on 2008-08-24
Running Ubuntu 8.04. I've been trying to listen to Resonance FM through Firefox. It streams as mp3.m3u, and Firefox wants to open it using LinDVD as default. But I'm told it's an 'unplayable file' by LinDVD. I know i can access default player settings at 

sudo gedit /etc/gnome/defaults.list

but which one would i change? Or is there another, even easier, solution?

---

### Post by owenll on 2008-08-24
This stream on Resonance FM plays with Amarok and VLC media player: 
[http://icecast.commedia.org.uk:8000/resonance_hi.mp3.m3u](http://icecast.commedia.org.uk:8000/resonance_hi.mp3.m3u)

---

### Post by owenll on 2008-08-24
Sorry - just realised you want to listen through Firefox - Mplayer plugin plays it on my computer.

---

### Post by amplexus on 2008-08-24
Thanks, that's it. I thought I had the plugin already, but hadn't after all.

---

### Post by Rognalf on 2008-09-19
I had a problem playing .m3u from emusic, and found this thread.
Did sudo gedit /etc/gnome/defaults.list and added line -
audio/x-m3u=totem.desktop
-just above the one for mp3. Works like a charm:-)

---

