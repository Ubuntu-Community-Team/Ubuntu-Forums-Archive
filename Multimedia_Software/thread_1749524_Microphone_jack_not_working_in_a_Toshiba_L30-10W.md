---
title: "Microphone jack not working in a Toshiba L30-10W"
date: 2011-05-04
forum: Multimedia Software
---

### Post by hotweiss on 2011-05-04
I just installed Ubuntu 11.04 onto a Toshiba L30-10W.  The built-in speakers work and the headphone jack work, but I can't get the microphone jack to work.  I've tried all of the ALSA options (e.g.- options snd-hda-intel model=laptop), but none of them have helped.  Any ideas?

---

### Post by lidex on 2011-05-04
What is your amixer output:
```
amixer
```

---

### Post by hotweiss on 2011-05-04
> **lidex said:**
> What is your amixer output:
```
amixer
```

```
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 64 [100%] [0.00dB] [on]
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
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [off]
  Front Right: Playback 31 [100%] [12.00dB] [off]
Simple mixer control 'Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 3 [100%] [30.00dB]
  Front Right: 3 [100%] [30.00dB]
Simple mixer control 'Beep',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 16 [52%] [10.50dB] [on]
  Front Right: Capture 16 [52%] [10.50dB] [on]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Internal Mic'
  Item0: 'Mic'
Simple mixer control 'Internal Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Internal Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%] [0.00dB]
  Front Right: 0 [0%] [0.00dB]
```

After some more fiddling around, I can now provide you some more information.  When I use the Google Talk plug-in in Gmail or Skype, people hear me, but my voice is extremely distorted. Meaning that they can just hear some sounds from my end. So I don't think it's a problem with my Alsa mixer levels.  It's weird, the problem only manifests itself in those two applications.  The microphone works with the Sound Recorder application.  My other computer is able to make calls over Skype without problems, so it's not an internet connection problem.

---

### Post by lidex on 2011-05-04
Which mic are you trying to use, internal? Take a close look at the mixer settings.

---

### Post by hotweiss on 2011-05-05
> **lidex said:**
> Which mic are you trying to use, internal? Take a close look at the mixer settings.

I am using the analog mic. Oh well, my previous Toshiba also had a tonne of Linux gremlins.  Mind you, there was a work around for all of them.

---

### Post by lidex on 2011-05-05
> After some more fiddling around, I can now provide you some more information. When I use the Google Talk plug-in in Gmail or Skype, people hear me, but my voice is extremely distorted. Meaning that they can just hear some sounds from my end. So I don't think it's a problem with my Alsa mixer levels. It's weird, the problem only manifests itself in those two applications. The microphone works with the Sound Recorder application. 
Then I would suspect settings/compatibility of the problematic software. Did you disable skype setting to allow control of mixer levels?

---

### Post by hotweiss on 2011-05-06
I fixed the issue by following these steps:

1) ```
sudo gedit /etc/modprobe.d/alsa-base.conf
```

2) Add the following two lines to the end:

```
options snd-card-0 index=0 
options snd-hda-intel index=0
```

---

