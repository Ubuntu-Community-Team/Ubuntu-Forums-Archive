---
title: "Getting digital sound from spdif on HDA ATI SB"
date: 2008-06-05
forum: Multimedia Software
---

### Post by danode on 2008-06-05
### I solved it, alsamixer is not very smart not to enable digital sound as default :P ###

Hi, i have been reading these forums as well as been googling like mad for 10 days now. I just cant get the spdif out to work. I dualboot with winXP for reference and there i have digital sound so i know it can work :)

Im running Ubuntu Hardy 8.04

Its built-in-sound on a MS K9AGM2 motherboard. 

The Coaxial spdif connection is wired from GRND and SPDIF OUT on motherboard, aka "optional spdif out bracket" according to motherboard manual

I have analog sound from headphone jack.

I have tried to manualy install Linux_503 driver from realtek web, but installation fails. (with install script provided in package)

This is info i have:
daniel@gandalf:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC888

daniel@gandalf:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

alsamixer
Card: HDA ATI SB
Chip: Realtek ALC888
View: [Playback] Capture  All
Item: Master [dB gain=0.00]

I would really appreciate help. ](*,)

Regards
Daniel

---

