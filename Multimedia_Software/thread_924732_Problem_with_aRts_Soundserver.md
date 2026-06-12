---
title: "Problem with aRts Soundserver"
date: 2008-09-19
forum: Multimedia Software
---

### Post by PieSquared on 2008-09-19
Hmm... I seem to be having a problem with the sound server.

Every so often, the sound server seems to stop working - and the next song I play fails. If it's in Amarok, I get the infamous "xine could not initialize audio drivers" message, if it's in Firefox then sound just doesn't play and sometimes causes FF to segfault, and if it's in mplayer it tells me:

```

AO: [pulse] Failed to connect to server: Connection refused
[AO_ALSA] alsa-lib: pcm_hw.c:1099:(snd_pcm_hw_open) open /dev/snd/pcmC0D0p failed: Device or resource busy
[AO_ALSA] alsa-lib: pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
[AO_ALSA] Playback open error: Device or resource busy
[AO OSS] audio_setup: Can't open audio device /dev/dsp: Device or resource busy
[AO_ALSA] alsa-lib: pcm_hw.c:1099:(snd_pcm_hw_open) open /dev/snd/pcmC0D0p failed: Device or resource busy
[AO_ALSA] alsa-lib: pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
[AO_ALSA] Playback open error: Device or resource busy
mcop warning: user defined signal handler found for SIG_PIPE, overriding
[AO ARTS] can't connect to aRts soundserver


```

I've tried a few things, including playing around with pulseaudio, oss, and alsa, and re-modprobing the drivers and such. However, after this problem arises, only a reboot can fix it (switching to KDE or anything doesn't help, only a full reboot.)

It usually only happens when songs are switching or starting.

Anyone have any ideas?
Thanks!

---

