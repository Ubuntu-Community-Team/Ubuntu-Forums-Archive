---
title: "Sound through NVIDIA HDMI"
date: 2009-07-25
forum: Multimedia Software
---

### Post by vggonz on 2009-07-25
Hi!

I'm new to these forums, although i've using GNU/Linux and Ubuntu for some years (I mean I'm not afraid of a manual kernel recompilation).

I'm not capable of getting sound through the HDMI connector of my graphics card, altough i'm getting HD video perfectly to my LCD TV (using VDPAU and 185.18.14 drivers from some repository). 

My graphics card is 

```
01:00.0 VGA compatible controller: nVidia Corporation G94 [GeForce 9600 GT] (rev a1)
```and my sound card is integrated on my MoBo (Asus P5Q-SE) and reported as

```
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
```I've manually upgraded ALSA to 1.0.20 from the default Jaunty version
```

me@pc:~$ cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.20.
Compiled on Jul 25 2009 for kernel 2.6.28-13-generic (SMP).
```but "aplay -l" reports only analog and digital out (from the sound card I suppose):

```
tarjeta 0: Intel [HDA Intel], dispositivo 0: ALC1200 Analog [ALC1200 Analog]
  Subdispositivos: 0/1
  Subdispositivo #0: subdevice #0
tarjeta 0: Intel [HDA Intel], dispositivo 1: ALC1200 Digital [ALC1200 Digital]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
```and "aplay -L" shows:

```
default:CARD=Intel
    HDA Intel, ALC1200 Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC1200 Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)
```No sign for anything of the HDMI output of my graphics card. As far as I have searched "aplay -l" should show something like this:

```
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```Play though the existent SPDIF/Digital output (mplayer -ao alsa:device=iec958 ) plays nothing to analog speakers or TV connected to HDMI. Do I miss a phisical connector between graphics card and MoBo for digital sound?

. I don't even know what to try. Please, any ideas?

---

