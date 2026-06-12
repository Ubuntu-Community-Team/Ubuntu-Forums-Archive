---
title: "headphones not working"
date: 2014-08-16
forum: Multimedia Software
---

### Post by tauchlack on 2014-08-16
Hello,

The internal speakers on my Dell laptop work fine. When the headphones are plugged in the speakers are muted but no sound goes through the headphones.  I have tried various workarounds including the sound troubleshooting procedure posted on this forum but nothing has worked so far.  Nothing.   Please help.

Here is the link to the alsa info: [http://www.alsa-project.org/db/?f=b7cb6151c13ad3d49279fc6ff443498cfc454b86](http://www.alsa-project.org/db/?f=b7cb6151c13ad3d49279fc6ff443498cfc454b86)

Many thanks.

---

### Post by tgalati4 on 2014-08-16
Check the BIOS for something called "Safety Mute" and turn it off.  It's designed for muting the system in case your headphones get unplugged while you are on a plane and are watching an air disaster movie.

---

### Post by tauchlack on 2014-08-17
I have looked at the BIOS but there is nothing there regarding sound.  I have also reinstalled Alsa and PulseAudio, played with the Alsa mixer, and tried a few other fixes, all to no avail.  This is the second pair of headphones I am trying to get working.

---

### Post by tgalati4 on 2014-08-17
Open a terminal and post the output of:

```
amixer
```

You should have at least:

> 
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]


I'm not sure what penum is (perhaps pulseaudio device enumeration), but pvolume and pswitch means that pulseaudio can control the volume and switch between them.

It's possible that your headphone jack is worn out.  There is a detection switch (either a physical disconnect tab) or a solid-state switch inside the sound chipset that allows automatic switching between the internal speakers and headphones.  When that switch is broken, you either don't get the switch or you get sound out of both speakers and headphones.  It's possible the solid-state switch can get blown with static electricity from plugging in headphones--especially on older machines.

If this machine is dual-boot, try testing under Windows or booting with a Live USB stick and see if it works.

---

### Post by tauchlack on 2014-08-17
Not dual-boot.
Here it is, thanks for the help:

Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 74
  Mono: Playback 48 [65%] [-26.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 74
  Mono:
  Front Left: Playback 74 [100%] [0.00dB] [on]
  Front Right: Playback 74 [100%] [0.00dB] [on]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 74
  Mono:
  Front Left: Playback 74 [100%] [0.00dB] [on]
  Front Right: Playback 74 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 4
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]
Simple mixer control 'Beep',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 3
  Mono: Playback 0 [0%] [-18.00dB] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 80
  Front Left: Capture 80 [100%] [6.00dB]
  Front Right: Capture 80 [100%] [6.00dB]
Simple mixer control 'Auto-Mute Mode',0
  Capabilities: enum
  Items: 'Disabled' 'Enabled'
  Item0: 'Enabled'

It didn't take long for the headphones jack to stop working.  I bought this machine and pretty much installed Linux right from the start.  After a month or two the sound just stopped.  There is a hissing sound in one of the earpieces.  A fresh Ubuntu install doesn't help either.

---

