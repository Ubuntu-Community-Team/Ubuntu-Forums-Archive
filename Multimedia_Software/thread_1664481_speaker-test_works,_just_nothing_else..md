---
title: "speaker-test works, just nothing else."
date: 2011-01-11
forum: Multimedia Software
---

### Post by callecx on 2011-01-11
ubuntu 10.10.

speaker-test works fine and i hear the correct sound out of each. However every other application i try to use audio with fails. I'm wanting to run xbmc and i cannot get any sound out of xbmc at all, unless i go with the digital output stereo option in system->prefs->sound. I currently have analog 5.1 surround sound selected (there is not digital option, besides stereo). i think the problem lies with pulseaudio?

$ speaker-test -Dhdmi:Intel -c6 -twavq

speaker-test 1.0.23

Playback device is hdmi:Intel
Stream parameters are 48000Hz, S16_LE, 6 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 349504
Period size range from 32 to 174752
Using max buffer size 349504
Periods = 4
was set period_size = 174752
was set buffer_size = 349504
 0 - Front Left
 4 - Centre
 1 - Front Right
 3 - Rear Right
 2 - Rear Left
 5 - LFE
Time per period = 21.892163

---

