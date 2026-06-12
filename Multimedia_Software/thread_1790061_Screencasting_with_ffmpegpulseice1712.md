---
title: "Screencasting with ffmpeg/pulse/ice1712"
date: 2011-06-24
forum: Multimedia Software
---

### Post by nicks27 on 2011-06-24
I'm trying to do screencasting as described here:
    **HOWTO: Proper Screencasting on Linux  **
    [http://ubuntuforums.org/showthread.php?t=1392026](http://ubuntuforums.org/showthread.php?t=1392026)
and I've managed to capture video but no audio.

I can hear the sound being played, and see it in the Envy24control application volume meters (it's an ICE1712 soundcard, a Terratec DMX-6fire), but there is no visible audio activity in the PulseAudio volume control application.

I figure I either need to somehow activate the soundcard in Pulse (but I have no idea how), or find some other options to pass to the ffmpeg command (other than "-f alsa -ac 2 -i pulse") to capture the audio from somewhere other than Pulse (but I don't know how to find out what parameters to pass).

Any ideas please?

---

