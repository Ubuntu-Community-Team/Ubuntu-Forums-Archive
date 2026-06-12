---
title: "SPDIF output to 9500GT"
date: 2010-08-23
forum: Multimedia Software
---

### Post by Paullus_N on 2010-08-23
Hi all,

short story first:
I need to get the audio output set to the SPDIF output on my motherboard.
That is the only way to get sound over the HDMI cable connected to my 9500GT.

I've tried several things, with no result but a clean installation of Ubuntu 10.04.
In this fresh installation I have updated Alsa to to version: 1.0.23

The Nvidia driver I'm using is 173.14.22

aplay -l:
> **** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1818S Analog [VT1818S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: SB [HDA ATI SB], device 1: VT1818S Digital [VT1818S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
aplay -L
> null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=SB
    HDA ATI SB, VT1818S Analog
    Default Audio Device
front:CARD=SB,DEV=0
    HDA ATI SB, VT1818S Analog
    Front speakers
surround40:CARD=SB,DEV=0
    HDA ATI SB, VT1818S Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=SB,DEV=0
    HDA ATI SB, VT1818S Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=SB,DEV=0
    HDA ATI SB, VT1818S Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=SB,DEV=0
    HDA ATI SB, VT1818S Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=SB,DEV=0
    HDA ATI SB, VT1818S Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=SB,DEV=0
    HDA ATI SB, VT1818S Digital
    IEC958 (S/PDIF) Digital Audio Output
In the sound config I have set the output to IEC985.
But still no sound,

Done all the things in this guide that applied to my system: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

It seems a lot of people have trouble with this, and most seem to be able to find a solution. I've tried most of them in previous installations. 

I'm not a complete noob with Linux, but no expert. So if I need to provide more information I would like the terminal command for it :)
And yes, I need the SPDIF output since my tv does a lot of image-correction and thus lags behind the sound. This is the only way to get both in sync.

TIA!

---

### Post by Paullus_N on 2010-10-14
bump?

---

