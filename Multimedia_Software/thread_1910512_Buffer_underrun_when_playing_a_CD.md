---
title: "Buffer underrun when playing a CD"
date: 2012-01-17
forum: Multimedia Software
---

### Post by rafe101 on 2012-01-17
I finally put a disc drive in my myth machine, but when testing it with a CD I'm getting pauses every 20 seconds or so. It's caused by a buffer underrun error. I have seen this error in my logs before ("ALSA, Error: Unable to sufficiently increase ALSA hardware buffer size - underruns are likely") with liveTV, but it didn't cause problems like this. Is there anyway to fix wha'ts going on?

```
2012-01-17 13:50:03.962 Pulse: PulseAudio suspend OK
2012-01-17 13:50:03.999 AO: Resampling from 44 kHz to 48 kHz with quality high
2012-01-17 13:50:04.000 AO: Opening audio device 'plughw:CARD=CMI8768,DEV=1' ch 6(2) sr 48000 sf signed 16 bit reenc 0
2012-01-17 13:50:04.003 ALSA, Error: Setting hardware audio buffer size to 128
2012-01-17 13:50:04.003 ALSA, Error: Error opening /proc/asound/card0/pcm1p/sub0/prealloc: Permission denied. 
2012-01-17 13:50:04.003 ALSA, Error: Try to manually increase audio buffer with: echo 128 | sudo tee /proc/asound/card0/pcm1p/sub0/prealloc
2012-01-17 13:50:04.003 ALSA, Error: Unable to sufficiently increase ALSA hardware buffer size - underruns are likely
2012-01-17 13:50:34.274 ALSA, Error: WriteAudio: buffer underrun
2012-01-17 13:50:51.520 ALSA, Error: WriteAudio: buffer underrun
2012-01-17 13:51:08.937 ALSA, Error: WriteAudio: buffer underrun
2012-01-17 13:51:26.395 ALSA, Error: WriteAudio: buffer underrun
2012-01-17 13:51:43.367 ALSA, Error: WriteAudio: buffer underrun
2012-01-17 13:52:00.300 ALSA, Error: WriteAudio: buffer underrun
2012-01-17 13:52:17.355 ALSA, Error: WriteAudio: buffer underrun
2012-01-17 13:52:34.844 ALSA, Error: WriteAudio: buffer underrun
2012-01-17 13:52:52.193 ALSA, Error: WriteAudio: buffer underrun
2012-01-17 13:53:09.388 ALSA, Error: WriteAudio: buffer underrun
2012-01-17 13:53:26.737 ALSA, Error: WriteAudio: buffer underrun
2012-01-17 13:53:44.125 ALSA, Error: WriteAudio: buffer underrun
2012-01-17 13:54:01.434 ALSA, Error: WriteAudio: buffer underrun
2012-01-17 13:54:18.883 ALSA, Error: WriteAudio: buffer underrun
```

---

