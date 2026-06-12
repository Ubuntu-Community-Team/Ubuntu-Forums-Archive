---
title: "Amarok hangs during normal usage"
date: 2006-10-25
forum: Multimedia &amp; Video
---

### Post by DigitalAxis on 2006-10-25
I've been using Xubuntu 6.06.1 on my laptop (Inspiron 8500, nVidia GeForce Ti 4200 Go, Sigmatel STAC audio) for a while now, and I'm having trouble with Amarok hanging on my system. (Amarok 1.4.1, from Kubuntu.org's repositories, with the corresponding amarok-xine engine)

The only generalizations I can really say (because I haven't been watching it carefully lately) are that it (always?) hang when it's not in the active virtual desktop.  Symptoms are, the windows don't repaint any more, the title bar doesn't change, and at the end of the *next* song, Amarok just goes silent.  It plays an entire song once hung.  This can happen anywhere between 15 and 300 minutes (usually about 15) after I start a dynamic playlist going, but it's guaranteed. (and then it's impossible to kill with killall -9, for some reason- I have to use kill and type the first Amarok PID I find.)

For a while I was linking this to xscreensaver activating, but I'm no longer quite as sure.  On the other hand, I just realized it's hanging now,  and I know both files were Ogg Vorbis.  Plus, it was on this virtual desktop obscured by this very Firefox window.

My music collection is something like 75% Vorbis, 25% MP3, with a couple MP2 files lying around.

Anyway, I'd like to know if anyone has experienced similar problems, and if there's any way to fix them.  Is the problem Amarok? Xine? Xubuntu?  The fact that I've got one of Kubuntu.org's special versions?

I'm getting really annoyed at it crashing so frequently.

---

### Post by foetusincome on 2006-12-18
I have the same problem.  During playback amarok, will simply freeze and I'll have to kill it.  Sometimes it takes 30 mins for this to happen or all day for this to happen.  I'm using amarok 1.4.4 on Kubuntu Edgy with a collection made up of mp3s, but i also had this problem with earlier versions.

---

