---
title: "When I press mute on gxine everything goes mute"
date: 2008-11-01
forum: Multimedia Software
---

### Post by AJ1000 on 2008-11-01
I am a newbie, and have found ubuntu (gnome version) great apart from how mute works.

Basically the problem is that if I have multiple things running (e.g. vlc, gxine, etc) and I press the mute button on gxine, everything goes mute (rather than just that particular gxine window).

System>Preferences>Sound has everything set to ALSA. This is what is on the tab:

Sound Playback - ALSA - Advanced Linux Sound Architecture (for all the Sound Playback options)
Sound Capture - ALSA - Advanced Linux Sound Architecture

Device - NVidia nForce2 (Alsa Mixer)
and finally in the combobox Master is highlighted.

Please help me so when I press mute in a particular application, only that application is muted rather than everything getting muted (as though I was using the master volume control).

What have I done wrong?

---

### Post by ajgreeny on 2008-11-01
Try using pulse audio as your default in System->Preferences->Sound.  That may work for you: it doesn't seem to for everybody, however, if no good go back to alsa again.

---

### Post by AJ1000 on 2008-11-01
Sorry, that did not make any difference, I dont think pulse audio works.

---

