---
title: "ALSA, OSS and PulseAudio all broken"
date: 2010-01-19
forum: Multimedia Software
---

### Post by HyperHacker on 2010-01-19
Seems every time I upgrade Xubuntu, sound gets broken somehow. This time, all three methods are not working in mplayer or mpd.

PulseAudio works for a bit, then crashes playing breakfast cereal sounds as reported [here](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/509493).

ALSA plays for 10 seconds, then mplayer locks up.

OSS does not play at all:```
[AO OSS] audio_setup: Can't open audio device /dev/dsp: Device or resource busy
Failed to initialize audio driver 'oss'
Could not open/initialize audio device -> no sound.
```

All three were working in 9.04.

---

