---
title: "HDMI audio sample rate problem"
date: 2010-11-04
forum: Mythbuntu
---

### Post by rburt on 2010-11-04
I have a 10.10 frontend setup to output digital sound via HDMI.  My recordings work fine...video and sound.  However anything that was originally 44.1kHz audio has no sound.  I'm sure my TV is expecting 48kHz audio.  This is my current asound.conf
```
pcm.!default {
        type hw
        card 0
        device 3
}
ctl.!default {
        type hw
        card 0
}

```If I add "rate 48000" to this asound.conf, my mp3's and videos will play sound, but I loose sound on my recordings.  So I'm sure the rate thing is my problem.

I thought Mythtv was supposed to resample everything to 48kHz.  In fact in 9.04 (my previous system) everything worked...recordings, video and mp3's.  I think I've tried every combination of settings in Mythtv's audio setup page but nothing seems to work.

Any help troubleshooting or suggestions would be much appreciated.  I need to have audio working for everything.  TIA.

Output from aplay -l and aplay -L
```
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

``````
null
    Discard all samples (playback) or generate zero samples (capture)
front:CARD=NVidia,DEV=0
    HDA NVidia, ALC889A Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, ALC889A Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, ALC889A Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, ALC889A Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, ALC889A Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, ALC889A Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=NVidia,DEV=0
    HDA NVidia, ALC889A Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
dmix:CARD=NVidia,DEV=0
    HDA NVidia, ALC889A Analog
    Direct sample mixing device
dmix:CARD=NVidia,DEV=1
    HDA NVidia, ALC889A Digital
    Direct sample mixing device
dmix:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    Direct sample mixing device
dsnoop:CARD=NVidia,DEV=0
    HDA NVidia, ALC889A Analog
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=1
    HDA NVidia, ALC889A Digital
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    Direct sample snooping device
hw:CARD=NVidia,DEV=0
    HDA NVidia, ALC889A Analog
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=1
    HDA NVidia, ALC889A Digital
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    Direct hardware device without any conversions
plughw:CARD=NVidia,DEV=0
    HDA NVidia, ALC889A Analog
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=1
    HDA NVidia, ALC889A Digital
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=3
    HDA NVidia, NVIDIA HDMI
    Hardware device with all software conversions
```

---

### Post by rburt on 2010-11-07
A little more info:

Myth version:  Version: 0.23.1+fixes26437-0ubuntu1

Alsa verseion:  1.0.23

I also tried the following asound.conf with the same results...no audio from 44.1kHz source files.

```
pcm.digital
        {
        type hw
        card 0
        device 3
}

pcm.!default {
        type plug
        slave.pcm digital
}

ctl.!default {
        type hw
        card 0
}

```Any help would be much appreciated.

---

