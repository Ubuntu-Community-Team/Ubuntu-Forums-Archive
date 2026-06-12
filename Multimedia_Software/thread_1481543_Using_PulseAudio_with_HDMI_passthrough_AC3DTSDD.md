---
title: "Using PulseAudio with HDMI passthrough AC3/DTS/DD"
date: 2010-05-12
forum: Multimedia Software
---

### Post by coolfrood on 2010-05-12
Hi,

I'm trying to get passthrough AC3/DTS working through NVidia HDMI.  The problem, as far as I can understand it, is that PulseAudio currently does not support passthrough.  There have been solutions posted in the past where people have managed to get passthrough working by taking away the IEC958 S/PDIF outputs from PulseAudio and going through ALSA directly for passthrough.

AFAIK, this is not possible with HDMI because I want to use PulseAudio for 2ch sound and straight ALSA for 5.1 passthrough sound.  For now, I got rid of PulseAudio, but this isn't an ideal situation because applications seem to be becoming dependent on PulseAudio.  For instance, I cannot figure out a configuration where I can get Boxee or xbmc to work properly in all cases.

Any ideas?

---

### Post by lidex on 2010-05-13
Over my head...maybe these will help:
[http://alsa.opensrc.org/DigitalOut]("http://alsa.opensrc.org/DigitalOut")
[http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240]("http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240")
[http://forum.xbmc.org/showthread.php?t=59877]("http://forum.xbmc.org/showthread.php?t=59877")
[http://ubuntuforums.org/showthread.php?t=1466111]("http://ubuntuforums.org/showthread.php?t=1466111")
[http://www.mythtv.org/wiki/Configuring_Analog_Sound_DVI_to_HDMI]("http://www.mythtv.org/wiki/Configuring_Analog_Sound_DVI_to_HDMI")

---

### Post by xzero1 on 2010-05-13
> AFAIK, this is not possible with HDMI because I want to use PulseAudio for 2ch sound and straight ALSA for 5.1 passthrough sound.

Why is it not possible? As I understand it, pulseaudio does not restrict alsa in any way. I use pulseaudio for normal sound but play 5.1 sound with alsa passthrough. The application has to support it though. As an example: 

```
mplayer -ao alsa:device=hw=0.2  -ac hwdts,hwac3 heart.ts
```

This code will play the heart.ts 5.1 video file using alsa hardware passthrough. The device specifics (0.2) may need to be changed depending on your hardware. See my post in this thread:

[http://ubuntuforums.org/showthread.php?p=9206877#post9206877]("http://ubuntuforums.org/showthread.php?p=9206877#post9206877")

---

### Post by aceracer24 on 2010-05-13
I can't even get alsa to work with passthrough. I have tried every damn program out there that allows me to select alsa for sound and when it is selected, I get no sound or i get sound but it's not 5.1. I can't begin to tell you how frustrating pulseaudio has been. This has been one my own only real remaining issue with using linux.

---

### Post by xzero1 on 2010-05-13
> **aceracer24 said:**
> I can't even get alsa to work with passthrough. I have tried every damn program out there that allows me to select alsa for sound and when it is selected, I get no sound or i get sound but it's not 5.1. I can't begin to tell you how frustrating pulseaudio has been. This has been one my own only real remaining issue with using linux.

What are you trying to play? Have you tried mplayer? Is the source 5.1?

---

### Post by aceracer24 on 2010-05-15
Trying to play DVD movies. I have tried VLC, MPlayer, GNome MPlayer as well as a couple others. It just refused to play in 5.1.

---

### Post by xzero1 on 2010-05-15
> **aceracer24 said:**
> Trying to play DVD movies. I have tried VLC, MPlayer, GNome MPlayer as well as a couple others. It just refused to play in 5.1.

Many dvds have multiple sound tracks. If you hear audio while using passthrough on a particular dvd, then make sure you have selected the right sound track. To switch sound tracks with mplayer type '#' while playing the movie.

---

