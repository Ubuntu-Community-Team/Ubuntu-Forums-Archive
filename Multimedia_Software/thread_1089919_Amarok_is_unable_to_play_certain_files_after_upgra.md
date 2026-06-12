---
title: "Amarok is unable to play certain files after upgrading to KDE 4.2.1"
date: 2009-03-07
forum: Multimedia Software
---

### Post by mikerobinson on 2009-03-07
Amarok 2 used to work perfectly, but after a recent upgrade (I think it was to KDE 4.2.1), when I try to play audio files in Amarok 2 (e.g. mp3, ogg), I get the error message "Too many errors encountered in playlist. Playback stopped". I tried using both Xine and GStreamer and both have the same effect. Even streaming media does not work. However, .m4a files DO work, oddly enough. The files that don't work in Amarok, however, play fine in other programs (e.g. Rhythmbox, Mplayer, Totem, Listen Music Player). Kaffeine goes into a "codec package is already installed" loop and doesn't play the files. What could possibly be causing this?

---

### Post by adibudeen on 2009-03-08
I have the same problem.  I can no longer get the gstreamer backend of phonon to work, so I've got the Xine one playing through pulseaudio (not an ideal setup).

---

### Post by mikerobinson on 2009-03-16
bump

---

### Post by hoppy on 2009-05-03
Hi,

Any luck sorting this out?

---

### Post by mikerobinson on 2009-05-04
This seemed to fix itself after an upgrade about 3 weeks after I posted this thread. I am now able to play all of my audio files in Amarok 2.0.1 with no problem.

---

