---
title: "scripting alsaplayer in 8.04"
date: 2008-07-25
forum: Multimedia Software
---

### Post by orbeus on 2008-07-25
Hi.

Today upgraded to Hardy...

Tried to run an old script (worked fine in 7.04) to start music playing on a PCI card.

====================
#!/bin/sh

lounge_start() {
echo "Starting lounge..."
alsaplayer -d "hw:1,0" -P /usr/local/playlists/lounge.m3u &
}

lounge_stop() {
echo "Stopping lounge..."
killall alsaplayer
}

lounge_restart() {
lounge_stop
sleep 1
lounge_start
}

case "$1" in
'start')
lounge_start
;;
'stop')
lounge_stop
;;
'restart')
lounge_restart
;;
*)
lounge_start
esac
====================

but get this error:

Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

alsaplayer will play the playlist if started manually from the GUI but I would like to have it automated.

Any help greatly appreciated! 

Thanks

O

---

