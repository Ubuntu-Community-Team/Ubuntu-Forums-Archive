---
title: "No HDMI audio after upgrade to 10.04"
date: 2010-06-19
forum: Multimedia Software
---

### Post by korgman on 2010-06-19
I've had audio working over HDMI for over a year.  Today, I upgraded my mythbuntu distro to 10.04 and I have lost all audio.  I'm using HDMI.

It finds the device

```
matt@mythtv:/etc$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


matt@mythtv:/etc$ aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
front:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=NVidia,DEV=0
    HDA NVidia, ALC1200 Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output
matt@mythtv:/etc$ 


```

I get no sound when I run this:

```
matt@mythtv:/etc$ speaker-test -Dhdmi:NVidia -c6 -twavq

speaker-test 1.0.22

Playback device is hdmi:NVidia
Stream parameters are 48000Hz, S16_LE, 6 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 5440
Period size range from 32 to 2720
Using max buffer size 5440
Periods = 4
was set period_size = 1088
was set buffer_size = 5440
 0 - Front Left
 4 - Center
 1 - Front Right
 3 - Rear Right


```
I ran the alsa config script and my alsa settings are all loaded and visible at this link:
[COLOR="Blue"][http://www.alsa-project.org/db/?f=e4daf11d561ff9501b9b7c1f352e511ec05042bb](http://www.alsa-project.org/db/?f=e4daf11d561ff9501b9b7c1f352e511ec05042bb)
[/COLOR]
Is there something wrong with nvidia drivers?  I notice that the "Hardware Drivers" app doesn't list the version of the installed nvidia driver.  It used to say NVIDIA accelerated graphics driver (version 185).  Now it says (version current[Recommended])

---

