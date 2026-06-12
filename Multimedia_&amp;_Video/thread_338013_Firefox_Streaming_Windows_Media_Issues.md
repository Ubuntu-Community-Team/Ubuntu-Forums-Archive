---
title: "Firefox Streaming Windows Media Issues"
date: 2007-01-13
forum: Multimedia &amp; Video
---

### Post by shawn_duggan on 2007-01-13
I have tried just about everything I have found searching the forums here.  I am running Edgy and cannot get streaming windows media to work.  QuickTime works.  In my current state, I have installed everything from Automatix2 and then removed the totem-mozilla plugin as apparently it can cause conflicts.

Mplayer just hangs connecting to server.  If anyone can help I'd sure appreciate it.

---

### Post by bruenig on 2007-01-13
Do you have mozilla-mplayer, that is the best plugin, it covers almost all filetypes? Also, in firefox enter
```
about:plugins
```
and see what it says as far as windows media is concerned.

---

### Post by shawn_duggan on 2007-01-14
I have the mozilla-mplayer plugin installed ([followed these steps most recently]("http://www.ubuntugeek.com/fix-for-mplayer-in-firefox-under-ubuntu-is-not-working.html")).  Viewing the FF plugins shows I have the MPlayer Windows Media Player plugin.

Even after compiling from source as per [this how-to]("http://ubuntuforums.org/showthread.php?t=323181&highlight=mplayer+plugin"), streaming windows media still does not work.

---

### Post by shawn_duggan on 2007-01-14
[This]("http://ubuntuforums.org/showthread.php?p=1649012") finally fixed it for me.  The audio is a bit choppy, but at least I can hit the videos on nhl.com and cnn.com again.

---

