---
title: "Cannot fully mute internal Mic"
date: 2011-05-17
forum: Multimedia Software
---

### Post by Calcipher on 2011-05-17
I have recently purchased a external microphone that runs through the line in jack on my Lenovo W700 and I am having some problems disabling the internal microphone completely.  As you can see from the amixer output below, I have completely muted "Mic", "Docking Mic", and "Internal Mic".   If I go into any sort of audio program (Mumble's sound config and Audacity being the ones I've tested with) I can see constant noise coming in (even with my external mic disconnected)  which seems to be directly related to the internal microphone.  Brushing the microphone holes with my finger creates noise as does typing.  

With PCM set low in Alsa Mixer the noise is much lower, but if I, in order to hear things, turn PCM up, the noise gets much worse to the point that it frequently fills 2/3s of the audio input bar in Mumble.  I have tested in Windows; if I disable the internal microphone no sound continues to get through so I figure this is a problem related to some combination of things on the Ubuntu side.  

I am running 11.04 (in classic mode if that matters) and can provide any additional details that might be helpful. 

```

> amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 74
  Mono:
  Front Left: Playback 74 [100%] [0.00dB] [on]
  Front Right: Playback 74 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 183 [72%] [-14.40dB]
  Front Right: Playback 179 [70%] [-15.20dB]
Simple mixer control 'Mic',0
  Capabilities: volume pswitch penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 80
  Front Left: 80 [100%] [6.00dB] Playback [off]
  Front Right: 80 [100%] [6.00dB] Playback [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 3
  Mono: Playback 1 [33%] [-12.00dB] [on]
Simple mixer control 'Docking Mic',0
  Capabilities: volume pswitch penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 80
  Front Left: 80 [100%] [6.00dB] Playback [off]
  Front Right: 80 [100%] [6.00dB] Playback [off]
Simple mixer control 'Internal Mic',0
  Capabilities: volume pswitch penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 80
  Front Left: 0 [0%] [-74.00dB] Playback [off]
  Front Right: 0 [0%] [-74.00dB] Playback [off]

```

---

