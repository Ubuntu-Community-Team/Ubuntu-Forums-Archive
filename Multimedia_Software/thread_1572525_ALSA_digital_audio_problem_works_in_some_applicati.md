---
title: "ALSA digital audio problem: works in some applications but not others"
date: 2010-09-11
forum: Multimedia Software
---

### Post by abrav on 2010-09-11
I am having a confusing problem with digital audio (SPDIF) output that I cannot figure out. I get digital audio output from Firefox, watching for example youtube movies. But the output to ALSA:iec958 is unrecognized. I am trying to get MythTV working and need to be able to access the digital output. I have spent hours reading all kinds of howto's and threads, but ALSA setup is just too complicated for a newbie. I hope someone can put me on the right track?

output of aplay -l is
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

output of aplay -L is
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=SB
    HDA ATI SB, ALC889A Analog
    Default Audio Device
front:CARD=SB,DEV=0
    HDA ATI SB, ALC889A Analog
    Front speakers
surround40:CARD=SB,DEV=0
    HDA ATI SB, ALC889A Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=SB,DEV=0
    HDA ATI SB, ALC889A Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=SB,DEV=0
    HDA ATI SB, ALC889A Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=SB,DEV=0
    HDA ATI SB, ALC889A Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=SB,DEV=0
    HDA ATI SB, ALC889A Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=SB,DEV=0
    HDA ATI SB, ALC889A Digital
    IEC958 (S/PDIF) Digital Audio Output


if I run 
aplay -D ALSA:iec958 test.wav

I get the output 
ALSA lib pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM ALSA:iec958
aplay: main:608: audio open error: No such file or directory

The result is similar if I write ALSA:spdif instead of ...iec958


Maybe I should add that i removed Pulse audio with
sudo aptitude remove pulseaudio

---

### Post by CHaoSlayeR on 2011-04-14
Did you ever manage to get it working? As I am currently trying myself without success up to now.

---

