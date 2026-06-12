---
title: "Movie Player/Firefox glitch"
date: 2009-01-26
forum: Multimedia Software
---

### Post by Revenged on 2009-01-26
If I have a movie going in Movie Player, and open up Firefox for youtube, or a flash game, there is no sound. If I had Firefox open first, the movie won't play properly, and has no sound.

I have three Gstreamer plugins, and my settings are as follows:

**Movie Player:** (Edit > Preferences > Audio)
Audio Output Type: Stereo

**System > Preferences > Sound** (under devices)
Sound Events:
 Sound playback: Audodetect
Music And Movies:
 Sound playback: Autodetect
Audio Conferencing:
 Sound playback: Autodetect
 Sound capture: ALSA
Default Mixer Tracks:
 Device: Alsa mixer


Does anyone know why it would do this, and how to fix it?

---

### Post by Linuxdork on 2009-01-26
I had the same problem.  It's a pulseaudio thing.  In the end I followed this howto: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) and it fixed everything.

---

### Post by Revenged on 2009-01-26
Haha, got it all working.

Thanks a lot.

---

### Post by Linuxdork on 2009-01-26
No problem, I'm glad it's working for you.

---

