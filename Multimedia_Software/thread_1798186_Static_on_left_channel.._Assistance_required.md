---
title: "Static on left channel.. Assistance required"
date: 2011-07-06
forum: Multimedia Software
---

### Post by magnat007 on 2011-07-06
I have an Old NEC Powermate tower and I am running Ubuntu 10.10.

It was going good till today where the left channel only gets static.. its gets louder with Volume and I have changed speakers twice.. Same issue is occurring. Audio is still being played but distinct static can be heard only on the left channel..



List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Codec: SigmaTel STAC9221 A1

This is all the information I have...
Now I am not technically minded so if the fix involves me using Terminal to do something I will need clear instructions as I am a New Ubuntu user.

---

### Post by magnat007 on 2011-07-06
Anyone ? I would like to aleviate the annoying static promptly ?

---

### Post by lidex on 2011-07-08
Keywords 'old nec'
Solder joint maybe?
What is your amixer output:
```
amixer
```
Use a Terminal="Applications->Accessories->Terminal"

Try booting into live-session or windows and see if problem exists there.

---

### Post by magnat007 on 2011-07-12
simple mixer control 'Master',0
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
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Line Jack Mode',0
  Capabilities: enum
  Items: 'Mic In' 'Line In' 'Line Out'
  Item0: 'Line Out'
Simple mixer control 'Mic Jack Mode',0
  Capabilities: enum
  Items: 'Mic In' 'Line In' 'Line Out'
  Item0: 'Mic In'
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 14
  Front Left: Capture 6 [43%] [9.00dB] [off]
  Front Right: Capture 6 [43%] [9.00dB] [off]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 14
  Front Left: Capture 0 [0%] [0.00dB] [off]
  Front Right: Capture 0 [0%] [0.00dB] [off]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line'
  Item0: 'Mic'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line'
  Item0: 'Mic'
Simple mixer control 'Mux',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 2
  Front Left: Capture 0 [0%] [0.00dB]
  Front Right: Capture 0 [0%] [0.00dB]
Simple mixer control 'Mux',1
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 4
  Front Left: Capture 0 [0%] [0.00dB]
  Front Right: Capture 0 [0%] [0.00dB]
Simple mixer control 'Swap Center/LFE',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]

I would love to boot it into a Windows platform but she only runs Ubuntu 10.10

---

### Post by magnat007 on 2011-07-30
So  No one has Any Idea's ???

---

### Post by magnat007 on 2011-07-30
It is now only happening on Every 3rd Reboot

---

