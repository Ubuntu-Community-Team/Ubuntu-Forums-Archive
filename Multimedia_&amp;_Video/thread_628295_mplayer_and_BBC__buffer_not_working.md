---
title: "mplayer and BBC : buffer not working"
date: 2007-12-01
forum: Multimedia &amp; Video
---

### Post by BigAce on 2007-12-01
Hi
I've tried to use mplayer pluggin for mozilla to listen live BBC1 radio, unfortunatly, I've to relaunch the stream each 2 minutes.
I've followed recommandations explains here and here in the forum (as change /etc/mplayerplug-in.conf text with /home/my_computer/.mozilla/mplayerplug-in.conf text)
Here is my/etc/mplayerplug-in.conf and my  /home/my_computer/.mozilla/mplayerplug-in.conf text:
ao=alsa
cachesize=512
cache-percent=25
dload-dir=/home/my_computer
showtime=1
enable-wmp=1
enable-qt=1
enable-rm=1
enable-gmp=1
enable-mpeg=1
enable-mp3=1
enable-ogg=1
enable-smil=1
enable-helix=1
nomediacache=0
rtsp-use-tcp=0

I really don't know how to oblige mplayer to use buffer option.

---

