---
title: "Slow / Broken Sound"
date: 2009-07-22
forum: Multimedia Software
---

### Post by ahoyle on 2009-07-22
Hi All

Please forgive this posting but this is my first attempt at using Ubuntu.

I have installed version 9.04 on to an old lab top, so I can learn more about Ubuntu and so my two pre-school kids can surf the web. All looks great, expect the sound. When the Ubuntu starts up it make a "noise". I have try playing a MP3 file and realised the sound card seems to be working very very slowly.

My system is a 2.4GHz Pentium 4 MMX with 512MB. 

I have tried to follow the instruction in the
                                                                             [COLOR=navy]_**Comprehensive Sound Problem Solutions Guide v0.5e **_[/COLOR]

My results were :-

```
aplay -l 
**** List of PLAYBACK Hardware Devices ****
card 0: I82801CAICH3 [Intel 82801CA-ICH3], device 0: Intel ICH [Intel 82801CA-ICH3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

find /lib/modules | grep snd
Produced a long list of modules

lspci -v
part of a long list
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
    Subsystem: CLEVO/KAPOK Computer Device 8880
    Flags: bus master, medium devsel, latency 0, IRQ 11
    I/O ports at e400 [size=256]
    I/O ports at e600 [size=64]
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0
```I have also run the alsa info script. The results should be viewable at ;-

[http://www.alsa-project.org/db/?f=de10b5f8ad51f98578cdcb4ed84e9b3886bb0149](http://www.alsa-project.org/db/?f=de10b5f8ad51f98578cdcb4ed84e9b3886bb0149)

My sound card seem to try to play sounds. It is just so slow it is unusable. Every thing else in Ubuntu seem to run at reasonable speed ( open office etc.)

Any and all help welcome
Thanks in advance
A Hoyle

---

### Post by igorzwx on 2009-07-22
Perhaps, you have pulse.
It has nothing to do on the old box.

read this:
[Howto: OSS4 with Ubuntu Lite (Beta, netboot)]("http://www.4front-tech.com/forum/viewtopic.php?t=3237")
[http://www.4front-tech.com/forum/viewtopic.php?t=3237](http://www.4front-tech.com/forum/viewtopic.php?t=3237)

you can search my post, if you want to know more

---

### Post by igorzwx on 2009-07-22
it is not noise, by the way, it is artefacts.
it is a kind of irremovable noise, if you want.
Try to record something with Audacity, and check spectrogram.

Install Skype from Medibuntu repositories,
and call to a friend.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

