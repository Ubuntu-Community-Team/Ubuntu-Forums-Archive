---
title: "SPDIF with ASRock ION330 Ubuntu 9.10 and Boxee Media Center"
date: 2010-01-15
forum: Multimedia Software
---

### Post by darukka on 2010-01-15
Hi there, can't get my SPDIF Output on my ASRock ION330 to work... I used the Minimal Installation CD from Ubuntu to install Boxee on it, but I just can't get my SPDIF audio to work.

Here is what I installed:
> sudo apt-get install linux-sound-base alsa-base alsa-utils


Is that everything I need?

Here is some info:
```
aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```


> lspci -v

00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
	Subsystem: ASRock Incorporation Device 5890
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at fae78000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

The <access denied> is strange, but I added my user to the audio group

```
amixer scontrols
Simple mixer control 'Master',0
Simple mixer control 'PCM',0
Simple mixer control 'Front',0
Simple mixer control 'Surround',0
Simple mixer control 'Center',0
Simple mixer control 'LFE',0
Simple mixer control 'Line',0
Simple mixer control 'Mic',0
Simple mixer control 'Mic Boost',0
Simple mixer control 'IEC958',0
Simple mixer control 'IEC958 Default PCM',0
Simple mixer control 'IEC958',1
Simple mixer control 'Capture',0
Simple mixer control 'Capture',1
Simple mixer control 'Beep',0
Simple mixer control 'Input Source',0
Simple mixer control 'Input Source',1
```

Boxee Settings:
Audio output ------- Digital
Dolby Digital AC3 -------- yes
DTS ---------- yes
Audio output device ------------ default:CARD=NVidia
Passtrough output device ------- iec958:CARD=NVidia,DEV=0
Downmix multichannel audio to stereo ------------ yes

Do you guys have any idea what could be wrong? :-S

---

### Post by darukka on 2010-01-20
really no one here to help? that **** is driving me crazy, i think i tried all the tutorials and howtos out there for spdif, but nothing works at all...

---

### Post by sisyphus1978 on 2010-01-20
I have an asrock 330, but I'm running xbmc (9.11). SPDIF works fine (I set it to custom output and specify iec958). I don't know anything about boxee other than it's not as good as xbmc.

---

### Post by darukka on 2010-01-20
When you set it up, did you install the whole Ubuntu system, with Gnome and everything? Did it work out of the box or did you have to configure something?

---

### Post by dutchhome on 2010-01-25
I figured this out.. See if this helps:

[http://forum.boxee.tv/showthread.php?t=15130](http://forum.boxee.tv/showthread.php?t=15130)

---

