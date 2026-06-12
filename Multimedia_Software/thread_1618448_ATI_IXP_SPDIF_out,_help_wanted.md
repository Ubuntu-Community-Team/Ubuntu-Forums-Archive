---
title: "ATI IXP SPDIF out, help wanted"
date: 2010-11-10
forum: Multimedia Software
---

### Post by snokesmurf on 2010-11-10
I have tried for some time now to sort out how to get my SPDIF output to work on the onboard soundcard I have, but no avail. I would like all sounds to go out on the SPDIF, and I don't want anything to go out on the analog outputs. I have updated ALSA driver, and I see the soundcard in aplay -l, but it simply makes no sound. I know I had this working on the same motherboard 1,5 yarsago, but I had some other issues with graphic card and overscan which was simply not solvable, but that is sorted now. Got boxee installed and is "only" a SPDIF problem away from having a nice little media center on my TV.

```
jondol@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: IXP [ATI IXP], device 1: ATI IXP IEC958 [ATI IXP IEC958 (AC97)]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
jondol@ubuntu:~$ aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
front:CARD=IXP,DEV=0
    ATI IXP, ATI IXP AC97
    Front speakers
surround40:CARD=IXP,DEV=0
    ATI IXP, ATI IXP AC97
    4.0 Surround output to Front and Rear speakers
surround41:CARD=IXP,DEV=0
    ATI IXP, ATI IXP AC97
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=IXP,DEV=0
    ATI IXP, ATI IXP AC97
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=IXP,DEV=0
    ATI IXP, ATI IXP AC97
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
iec958:CARD=IXP,DEV=0
    ATI IXP, ATI IXP IEC958 (AC97)
    IEC958 (S/PDIF) Digital Audio Output

```More relevant info about the various things found here [http://www.alsa-project.org/db/?f=85420489f0b63a441bf6ed65f08356236f115992](http://www.alsa-project.org/db/?f=85420489f0b63a441bf6ed65f08356236f115992)

Hope someone can point me  a little bit in the right direction.

---

