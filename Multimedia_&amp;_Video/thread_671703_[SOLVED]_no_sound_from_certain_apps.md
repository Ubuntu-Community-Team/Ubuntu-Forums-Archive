---
title: "[SOLVED] no sound from certain apps"
date: 2008-01-18
forum: Multimedia &amp; Video
---

### Post by MangasColoradas on 2008-01-18
I might have caused this problem trying to get skype working, I also installed pulseaudio, which I have now uninstalled.

I have no sound from VLC and get an error when trying to play a video using mplayer movieplayer 'could not open/initialize audio device -> no sound', however I can stream BBC radio using mplayer?

I have sound from videos using totem movie player.

I get no log in sounds anymore.

I have tested the pipelines in 'sound preferences' and sounds are working there but not the login/out sounds.

---

### Post by MangasColoradas on 2008-01-18
Fixed it by reinstalling alsa, found this guide [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

Ubuntu kept crashing, maybe because it removes GDM too, it would have worked better from a failsafe terminal I guess.

---

