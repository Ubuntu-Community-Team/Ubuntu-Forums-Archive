---
title: "HDMI mono audio on shuttle SG33G5"
date: 2008-10-17
forum: Multimedia Software
---

### Post by mschrenk on 2008-10-17
I have installed ubuntu 8.10 beta for amd64 on a [Shuttle SG33G5]("http://global.shuttle.com/download03.jsp?PI=635&PL=2") and wish to use the HDMI port for sound and video.

Out of the box the video worked, however the best I can do with the audio is mono sound out of the left speaker.

I got to this point following parts of [a post describing disabling pulseaudio]("http://ubuntuforums.org/showpost.php?p=5453964&postcount=12").

Specifically I followed the steps:
1. System->Pref->Sessions->Startup Programs - Disable the pulseaudio related process.
2. System->Pref->Sessions->Startup Programs - add a new one with command "killall pulseaudio"

which got alsamixer to show the correct Chip: Silicon Image SiI1392 HDMI.

In System->Pref->Sound I selected "HDA Intel ATI HDMI (ALSA)" as my sound device and in alsamixer unmuted "IEC958 1"

So I now can get sound out of the left speaker, but cannot find any information on stereo sound.

Below is my amixer output, which shows that "IEC958 1" has only an mono output channel, is there any way to add stereo output?

```
:~$ amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 13 [42%] [-27.00dB] [off]
Simple mixer control 'Headphone',0
  Capabilities: pswitch
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [off]
  Front Right: Playback [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [0.00dB] [off]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 31
  Mono: Playback 31 [100%] [0.00dB] [off]
Simple mixer control 'Side',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [off]
  Front Right: Playback 31 [100%] [0.00dB] [off]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [off]
  Front Right: Playback 31 [100%] [12.00dB] [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [off]
  Front Right: Playback 31 [100%] [12.00dB] [off]
Simple mixer control 'Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 3 [100%]
  Front Right: 3 [100%]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined cswitch cswitch-joined
  Playback channels: Mono
  Capture channels: Mono
  Mono: Playback [on] Capture [on]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'IEC958',1
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Aux',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [off]
  Front Right: Playback 31 [100%] [12.00dB] [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 31 [100%] [30.00dB] [off]
  Front Right: Capture 31 [100%] [30.00dB] [off]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 31 [100%] [30.00dB] [off]
  Front Right: Capture 31 [100%] [30.00dB] [off]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Line' 'Aux'
  Item0: 'Mic'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Mic' 'Line' 'Aux'
  Item0: 'Line'

```

---

### Post by mschrenk on 2008-10-17
Ok after doing more searching it looks like alsa has open bugs for this, so I guess there is no fix yet.

[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2765](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2765)
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3754](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3754)

---

