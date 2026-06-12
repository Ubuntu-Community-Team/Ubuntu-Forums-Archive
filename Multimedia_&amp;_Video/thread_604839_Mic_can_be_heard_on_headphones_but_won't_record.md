---
title: "Mic can be heard on headphones but won't record"
date: 2007-11-06
forum: Multimedia &amp; Video
---

### Post by frankly.de on 2007-11-06
**This post could be related to an Ubuntu bug filed at**: [https://answers.launchpad.net/ubuntu/+question/17196](https://answers.launchpad.net/ubuntu/+question/17196) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Yes, I have seen countless posts with a similar problem, but none of their solutions seem to work for me.

Here is my case:
- version 7.10 on amd64 machine

- "cat /proc/asound/cards" produces the following output
       0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xc0000000 irq 16

- amixer gives the following details:
Simple mixer control 'Headphone',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 23
  Mono:
  Front Left: Playback 17 [74%] [15.00dB] [on]
  Front Right: Playback 17 [74%] [15.00dB] [on]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 23
  Mono:
  Front Left: Playback 23 [100%] [33.00dB] [off]
  Front Right: Playback 23 [100%] [33.00dB] [off]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 13
  Front Left: Capture 13 [100%] [33.00dB] [on]
  Front Right: Capture 13 [100%] [33.00dB] [on]
Simple mixer control 'Caller ID',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Digital',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 66 [55%] [3.00dB]
  Front Right: Capture 66 [55%] [3.00dB]
Simple mixer control 'Input Source',0
  Capabilities: enum
  Items: 'Mic' 'CD'
  Item0: 'Mic'
Simple mixer control 'Off-hook',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]

I can clearly hear the Mic input in the headphones, unless, of course, the mic is muted.
Volume Control (gnome-volume-control 2.20.1): Under "HDA ATI SB (Alsa mixer)" - my choice -  my volume control contains 4 Tabs: Playback (PCM, CD, Microphone), Recording (Capture, Digital), Switches (Headphones [checked], Front [checked], IEC958, Caller ID,Off-hook) and Options (Input Source is set to Microphone, other option is CD). Under "Realtek ALC861 (oss Mixer)" I have one tab with: Volume, Microphone, CD, PCM-2, In-gain, Digital-1.
In Sound Recorder (gnome-sound-recorder 2.20.1) the only input devices I can chose form are Capture and Digital.
In skype I have a choice of these Audio devices: default device (Default), HDA ATI SB in six different versions: hw;SB,0 / plughw;SB,0 / hw;SB,1 / plughw;SB,1 / hw;SB,6 / plughw;SB,6.  I also have alsa-base in Version 1.0.14, alsamixergui, alsaplayer-alsa and alsa-utils in the latest versions. 

Should any further Information be required, lease do not hesitate to ask! Thanks!

---

