---
title: "Problem with audio over HDMI with NVidia card"
date: 2011-08-07
forum: Multimedia Software
---

### Post by canbal on 2011-08-07
Hi everyone,

I am trying to connect my desktop computer to my TV and I need some assistance with using audio over HDMI. I have an NVidia 580 GTX graphics card and I am on Ubuntu 10.04. I compiled and upgraded to newest alsa, so my HDMI audio shows up as one of the sound cards. I also read that I should manually unmute everything that shows up in alsamixer that is related with the NVidia card, and I did that as well. Unfortunately I still don't have any audio.. :( I would appreciate any suggestion as I am quite unfamiliar with alsa and audio in Ubuntu. Thanks.

Here's the output of aplay:

```
$ aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
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
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, HDMI 0
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=1
    HDA NVidia, HDMI 0
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=2
    HDA NVidia, HDMI 0
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    HDMI Audio Output

```

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

---

### Post by BicyclerBoy on 2011-08-07
You would need to be running the latest nvidia graphics driver for that GPU.
nVidia 275 does support GTX580.

Make sure the HDMI device is powered up/connected as the X server starts.

speaker-test -c2 -r 48000 -D hw2:3
speaker-test -c2 -r 48000 -D hw2:7
speaker-test -c2 -r 48000 -D hw2:8
speaker-test -c2 -r 48000 -D hw2:9

and report which one produced pink noise..

Does speaker-test indicate the alsa driver version ?

---

### Post by canbal on 2011-08-07
> **BicyclerBoy said:**
> You would need to be running the latest nvidia graphics driver for that GPU.
nVidia 275 does support GTX580.

Make sure the HDMI device is powered up/connected as the X server starts.

speaker-test -c2 -r 48000 -D hw2:3
speaker-test -c2 -r 48000 -D hw2:7
speaker-test -c2 -r 48000 -D hw2:8
speaker-test -c2 -r 48000 -D hw2:9

and report which one produced pink noise..

Does speaker-test indicate the alsa driver version ?

Yes I am using NVidia 275.19 driver and my ALSA is the latest snapshot.

```
$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.24.
Compiled on Aug  7 2011 for kernel 2.6.32-33-generic (SMP).
```

This following command worked for me to get noise from the TV:

```
speaker-test -c2 -r 48000 -D plughw:2,7
```

So how do I set this up to be my default output for sound?

I feel I am close, one more push please... :)

---

### Post by canbal on 2011-08-07
I found this guide, [ftp://download.nvidia.com/XFree86/gpu-hdmi-audio-document/gpu-hdmi-audio.html]("ftp://download.nvidia.com/XFree86/gpu-hdmi-audio-document/gpu-hdmi-audio.html"), and followed the "13.9.1. Adding Extra Outputs To PulseAudio".


Adding ```
load-module module-alsa-sink device=hw:1,7
``` to [FONT="System"]/etc/pulse/default.pa[/FONT] made another HDA device to appear in my sound preferences. Selecting that as my output solved my problem.

---

### Post by BicyclerBoy on 2011-08-08
Good work..

---

