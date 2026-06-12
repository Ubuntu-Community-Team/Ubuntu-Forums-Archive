---
title: "How to get firefox plugins to work with wma streams"
date: 2006-12-05
forum: Multimedia &amp; Video
---

### Post by qiet72 on 2006-12-05
Hi,

I am trying to play some web-based network radio stations.  Some of them require a player capable of playing windows media streams.  I have used Automatix to install the necessary plugins, codecs, and players.  I can play wma files directly via mplayer/vlc/totem but I cannot play them via firefox and totem-xine plugin interface.

The first picture shows the error message when connecting to a radio station, the second picture shows what plugins are installed in firefox and the third shows the codecs installed in the system.

Any ideas to the error message?

qiet72

---

### Post by joselin on 2006-12-05
You must remove the actual totem pluggin for firefox and install the mplayer one.

```

apt-get install mozilla-mplayer

```

Regards

---

### Post by qiet72 on 2006-12-05
[QUOTE=joselin;1847331]You must remove the actual totem pluggin for firefox and install the mplayer one.

What is the package name to remove (sudo apt-get remove xxxxx) ?

I found out how: sudo rm /usr/lib/firefox/plugins/libtotem*
mozilla-mplayer is already installed: /usr/lib/firefox/plugins/mplayerplug-in-* exists.

Errors are gone now, but still no audio playback.

Qiet72

---

### Post by joselin on 2006-12-06
> **qiet72 said:**
> 
What is the package name to remove (sudo apt-get remove xxxxx) ?


You must remove totem-mozilla. It should work once you remove it if you have installed mozilla-mplayer.

Regards.

---

