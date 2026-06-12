---
title: "Microphone voice playback"
date: 2008-06-26
forum: Multimedia Software
---

### Post by supersmashbrothers on 2008-06-26
Well I want the microphone to play my voice instantly like it does on my desktop. It seems like my laptop sound does not include the option that mixes the output and the microphone from amixer. I have tested and tried Sound Recorder and I know that recording works 100%.

I wonder if there is any software that allows voice playback from the microphone mixing. I want this for karaoke.

amixer
```
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 16 [52%] [-22.50dB] [on]
  Front Right: Playback 16 [52%] [-22.50dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 8 [53%] [12.00dB] [on]
  Front Right: Capture 8 [53%] [12.00dB] [on]
Simple mixer control 'Capture Mux',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 4
  Front Left: 4 [100%] [40.00dB]
  Front Right: 4 [100%] [40.00dB]
Simple mixer control 'Digital',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 40 [33%] [-10.00dB]
  Front Right: Capture 40 [33%] [-10.00dB]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic'
  Item0: 'Mic'

```

amixer info
```
Card default 'Intel'/'HDA Intel at 0xefebc000 irq 20'
  Mixer name	: 'SigmaTel STAC9200'
  Components	: 'HDA:83847690 HDA:14f12bfa'
  Controls      : 12
  Simple ctrls  : 7

```

---

### Post by supersmashbrothers on 2008-07-07
Does anyone have any idea how to set this up?

---

