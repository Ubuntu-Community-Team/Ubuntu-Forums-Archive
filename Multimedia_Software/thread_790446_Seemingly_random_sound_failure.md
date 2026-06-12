---
title: "Seemingly random sound failure"
date: 2008-05-11
forum: Multimedia Software
---

### Post by araneae on 2008-05-11
My sound works most of the time.  However, sometimes it fails on rebooting.  Usually this is fixed by restarting the computer, but this is starting to get annoying.

When I try to play something, I get these errors:

alsa-lib: pcm_hw.c:1242:(snd_pcm_hw_open) open /dev/snd/pcmC0D0p failed: Device or resource busy
alsa-lib: pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
alsa-init: playback open error: Device or resource busy
[AO OSS] audio_setup: Can't open audio device /dev/dsp: Device or resource busy
alsa-lib: pcm_hw.c:1242:(snd_pcm_hw_open) open /dev/snd/pcmC0D0p failed: Device or resource busy
alsa-lib: pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
alsa-init: playback open error: Device or resource busy
[AO ARTS] Connected to sound server.
[AO ARTS] Stream opened.
[AO ARTS] buffer size: 20480
[AO ARTS] buffer size: 2048
AO: [arts] 48000Hz 2ch s16le (2 bytes per sample)

So far, I've tried restarting alsa-utils and reloading alsa-utils, but it doesn't fix the problem.  Only rebooting seems to.

Any ideas on possible causes/how to fix?  

Thanks!

---

### Post by deja on 2008-06-26
I know it has something to do with another process tying up the sound driver, but I don't remember how to fix it, and have been trying to find the fix that I know I've seen on here at some point.

---

