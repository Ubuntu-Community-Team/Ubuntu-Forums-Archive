---
title: "M-Audio Quattro in Alsamixer"
date: 2010-05-18
forum: Multimedia Software
---

### Post by cmpmj on 2010-05-18
Just trying to set this device up to playback via Alsamixer in Ubuntu 9.04

I get:

Sound playback: M Audio USB Quattro USB Audio (ALSA)

When I hit the test button I get silence plus:

Error:

audiotestsrc wave=sine freq=512 !
audioconvert ! audioresample ! gconfaudiosink:
Could not open audio device for playback.

Any idea how to set this up?

---

