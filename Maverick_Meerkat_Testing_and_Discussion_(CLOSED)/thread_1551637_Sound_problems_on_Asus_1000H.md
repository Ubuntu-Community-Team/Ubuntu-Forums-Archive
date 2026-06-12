---
title: "Sound problems on Asus 1000H"
date: 2010-08-12
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by zekopeko on 2010-08-12
I'm getting no sound although every volume level I could find shows it's not muted.

The sound device is:

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)

Anybody have any suggestions? I did try the sound troubleshooting guide from the wiki put it didn't help.

---

### Post by taavikko on 2010-08-12
Output of
```
aplay -l; aplay -L
```

Does the following produce a sound or anything?
```
aplay /usr/share/sounds/alsa/Front_Center.wav
```

---

### Post by zekopeko on 2010-08-12
> **taavikko said:**
> Output of
```
aplay -l; aplay -L
```

```
~$ aplay -l; aplay -L
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=Intel,DEV=0
    HDA Intel, ALC269 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC269 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC269 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC269 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC269 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC269 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers

```

> Does the following produce a sound or anything?
```
aplay /usr/share/sounds/alsa/Front_Center.wav
```

No sound on either the speakers or the headphones. Alsamixer has every volume (Master, Speaker, Headphones, PCM) set on max.

BTW when I tested if I was in the audio group I wasn't but another normal accounts was. I added myself to it but that didn't make a difference.

---

### Post by taavikko on 2010-08-13
You forgot to mention has the sound ever worked on that hardware?

If I remember correctly, permissions are given dynamically so no need to put users to groups, it shouldn't make a difference at all.

The following will give an detailed output of device 
```
amixer
```
It also shows the sound levels, if something is still muted?

ALC269 chips should work pretty well.
Allthough sometimes minor adjustements are required in some hardware.

```
ALC269
======
  basic         Basic preset
  quanta        Quanta FL1
  eeepc-p703    ASUS Eeepc P703 P900A
  eeepc-p901    ASUS Eeepc P901 S101
  fujitsu       FSC Amilo
  lifebook      Fujitsu Lifebook S6420
  auto          auto-config reading BIOS (default)
```

I would try adding the following line to /etc/modprobe.d/alsa-base.conf
```
options snd-hda-intel model=auto
```
and restart.

---

### Post by zekopeko on 2010-08-13
> **taavikko said:**
> You forgot to mention has the sound ever worked on that hardware?

If I remember correctly, permissions are given dynamically so no need to put users to groups, it shouldn't make a difference at all.

Yes it worked. The only problem I got since Lucid was that my speaker volume would be 0 on every reboot.

> The following will give an detailed output of device 
```
amixer
```
It also shows the sound levels, if something is still muted?

ALC269 chips should work pretty well.
Allthough sometimes minor adjustements are required in some hardware.

```
ALC269
======
  basic         Basic preset
  quanta        Quanta FL1
  eeepc-p703    ASUS Eeepc P703 P900A
  eeepc-p901    ASUS Eeepc P901 S101
  fujitsu       FSC Amilo
  lifebook      Fujitsu Lifebook S6420
  auto          auto-config reading BIOS (default)
```

I would try adding the following line to /etc/modprobe.d/alsa-base.conf
```
options snd-hda-intel model=auto
```
and restart.
```
~$ amixer 
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 64 [100%] [0.00dB] [off]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 63 [98%] [0.00dB] [off]
  Front Right: Playback 63 [98%] [0.00dB] [off]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [1.00dB] [off]
  Front Right: Playback 64 [100%] [1.00dB] [off]
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
  Front Left: 0 [0%]
  Front Right: 0 [0%]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 25 [54%] [8.00dB] [off]
  Front Right: Capture 25 [54%] [8.00dB] [off]

```

I did at the option snd-hda-intel to my alsaconf but it makes no difference.
BTW the sound works in Windows so it's not a hardware problem.

---

### Post by zekopeko on 2010-08-13
OK found out what the problem was. It was set to stream via DNLA/UPnP for some reason. It looks to work now.

Thank you for trying to help me.

---

