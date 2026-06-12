---
title: "sound problems"
date: 2009-10-17
forum: Multimedia Software
---

### Post by jrbless on 2009-10-17
I purchased an ASUS M3A78-EM motherboard for use in a MythTV frontend/backend system.  It is an install of the Mythbuntu 9.04 with all upgrades applied.  I was able to get the video and networking to work fine, but am having a problem with the audio - it only comes through in stereo and not surround.

The integrated audio chipset is a "Realtek ALC1200" and I am needing to use the spdif output (to connect to a home theater system).  I have installed the newest ALSA drivers that are available (alsa-driver-1.0.21 and alsa-firmware-1.0.20).

uname -a gives:
Linux MythTV 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009 i686 GNU/Linux


aplay -l gives:
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

aplay -L gives:
default:CARD=SB
    HDA ATI SB, ALC1200 Analog
    Default Audio Device
front:CARD=SB,DEV=0
    HDA ATI SB, ALC1200 Analog
    Front speakers
surround40:CARD=SB,DEV=0
    HDA ATI SB, ALC1200 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=SB,DEV=0
    HDA ATI SB, ALC1200 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=SB,DEV=0
    HDA ATI SB, ALC1200 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=SB,DEV=0
    HDA ATI SB, ALC1200 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=SB,DEV=0
    HDA ATI SB, ALC1200 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=SB,DEV=0
    HDA ATI SB, ALC1200 Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)


I've gone into alsamixer and unmuted everything, but I'm still only getting stereo sound.  I'm definitely a novice when it comes to this stuff, but I had seen the above commands run and the output seemed helpful to try debugging the problem.

Ideally, I would like to use AC3 and DTS passthrough for sound output.

If anyone can give me a pointer in how to proceed, I'd greatly appreciate it!
James

---

