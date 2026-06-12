---
title: "Sound only works as root.  (i3wm, user is in audio group)"
date: 2013-12-23
forum: Multimedia Software
---

### Post by sdouble on 2013-12-23
I'm running mpd + sonata and that works fine, but mpd runs as root.  running alsamixer under my user controls my volumes just fine while listening to mpd.  alsamixer has the correct output device selected.

here are groups my user belongs to: 
adm cdrom sudo audio dip plugdev fuse lpadmin sambashare pulse-access

I've removed myself from audio and pulse-access and readded, reinstalled alsa, relogged, rebooted, etc

firefox and chromium do not play sound on youtube, but if I run firefox as root - the sound works.

I'm running ubuntu minimal with i3.  I've searched the forum and found only things to check through the standard installation UI and group issues, I don't have unity and my user seems to be in the appropriate groups.  Any ideas?  Thanks!

---

