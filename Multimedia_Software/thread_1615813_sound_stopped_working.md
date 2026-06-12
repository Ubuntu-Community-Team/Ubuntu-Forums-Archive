---
title: "sound stopped working"
date: 2010-11-07
forum: Multimedia Software
---

### Post by me.translucent on 2010-11-07
One fine morning i switched on my laptop and the sound was gone .can't get any sound in movies / music /anything tried various players ,checked if its muted(no its not).Help!!!!

PS: My Ubuntu version is 10.10

---

### Post by I'mGeorge on 2010-11-07
when you play let's say an mp3 song in audacious do you get any error or it looks like the song it's played but nos sound comes out ?

---

### Post by me.translucent on 2010-11-07
Song is played without an error but no sound comes out.I even checked in the SoundPreferences->Hardware->TestSpeakers the test seems to work fine but the sound doesn't comes out.
Actually it got me suspicious and i booted into windows 7 to check if my speakers were okay(Yes they are).

---

### Post by I'mGeorge on 2010-11-07
It's not that I doubt you but would you please post the output of the command "amixer get Master && amixer get PCM && amixer get Front"

---

### Post by me.translucent on 2010-11-07
output:

```
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
amixer: Unable to find simple control 'Front',0
```

---

### Post by I'mGeorge on 2010-11-07
It should be Ok the Front option it's not mandatory but if you have it and it's on mute it won't "sing". Another thing do you have PulseAudio installed also ?

---

