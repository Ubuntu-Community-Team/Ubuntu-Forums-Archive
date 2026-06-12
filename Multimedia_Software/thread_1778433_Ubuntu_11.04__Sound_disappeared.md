---
title: "Ubuntu 11.04 / Sound disappeared"
date: 2011-06-09
forum: Multimedia Software
---

### Post by Monti_australia on 2011-06-09
Hello. I have Asus X52N notebook. Sound suddenly disappeared. It works now only with headphones. 
I'll appreciate your help.

---

### Post by lidex on 2011-06-10
Post your amixer output please:
```
amixer
```
In a terminal.

---

### Post by Monti_Anderson on 2011-06-10
amixer 

> Simple mixer control 'Master',0
Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
Playback channels: Mono
Limits: Playback 0 - 87
Mono: Playback 87 [100%] [0.00dB] [on]
Simple mixer control 'Headphone',0
Capabilities: pvolume pswitch penum
Playback channels: Front Left - Front Right
Limits: Playback 0 - 87
Mono:
Front Left: Playback 87 [100%] [0.00dB] [on]
Front Right: Playback 87 [100%] [0.00dB] [on]
Simple mixer control 'Speaker',0
Capabilities: pvolume pswitch penum
Playback channels: Front Left - Front Right
Limits: Playback 0 - 87
Mono:
Front Left: Playback 0 [0%] [-65.25dB] [off]
Front Right: Playback 0 [0%] [-65.25dB] [off]
Simple mixer control 'PCM',0
Capabilities: pvolume penum
Playback channels: Front Left - Front Right
Limits: Playback 0 - 255
Mono:
Front Left: Playback 255 [100%] [0.00dB]
Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Mic Boost',0
Capabilities: volume penum
Playback channels: Front Left - Front Right
Capture channels: Front Left - Front Right
Limits: 0 - 3
Front Left: 3 [100%] [36.00dB]
Front Right: 3 [100%] [36.00dB]
Simple mixer control 'Capture',0
Capabilities: cvolume cswitch penum
Capture channels: Front Left - Front Right
Limits: Capture 0 - 31
Front Left: Capture 25 [81%] [21.00dB] [on]
Front Right: Capture 25 [81%] [21.00dB] [on]
Simple mixer control 'Capture',1
Capabilities: cvolume cswitch penum
Capture channels: Front Left - Front Right
Limits: Capture 0 - 31
Front Left: Capture 0 [0%] [-16.50dB] [on]
Front Right: Capture 0 [0%] [-16.50dB] [on]
Simple mixer control 'Internal Mic Boost',0
Capabilities: volume penum
Playback channels: Front Left - Front Right
Capture channels: Front Left - Front Right
Limits: 0 - 3
Front Left: 3 [100%] [36.00dB]
Front Right: 3 [100%] [36.00dB]

---

### Post by lidex on 2011-06-12
Use alsamixer to adjust/unmute this element:
```
Simple mixer control 'Speaker',0
Capabilities: pvolume pswitch penum
Playback channels: Front Left - Front Right
Limits: Playback 0 - 87
Mono:
Front Left: Playback 0 [0%] [-65.25dB] [off]
Front Right: Playback 0 [0%] [-65.25dB] [off]
```

---

