---
title: "creative zen v plus"
date: 2010-08-06
forum: Multimedia Software
---

### Post by breek on 2010-08-06
a friend of mine (linux newbie) asked me for some help for using his creative zen v plus on ubuntu 10.04, so i've tried some programs... and that's the result:


- banshee
can connect with zen player and show the mp3s but can't play them, even ubuntu-restricted-extras, gstreamer-plugins-bad/ugly, fluendo-mp3 are installed


-exaile
ignores the zen player; there's no mtp plugin so i tried mass-storage but doesn't work (libmtp and mtp-tools are installed)


- rhythmbox
can connect with zen player and show the mp3s but can't play them, showing an error message (something like "no file specified for reading", free translation from italian message) and in terminal i get

(rhythmbox:2467): GStreamer-WARNING **: 
Trying to join task 0x9f2e928 from its thread would deadlock.
You cannot change the state of an element from its streaming
thread. Use g_idle_add() or post a GstMessage on the bus to
schedule the state change from the main thread.


- amarok
plays and copys mp3s on the device but has a known bug: the program doesn't quit (must be killed from terminal... can't be suggested to a newbie)


any ideas?

---

