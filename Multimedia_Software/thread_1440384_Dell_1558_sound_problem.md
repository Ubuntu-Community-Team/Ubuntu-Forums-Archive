---
title: "Dell 1558 sound problem"
date: 2010-03-27
forum: Multimedia Software
---

### Post by AntoniusUno on 2010-03-27
Hi guys,

I am having a Dell 1558 laptop with Window 7 and Ubuntu 9.10 dual boot and am having sound problems:

1. Dell function keys for VolumeUP, VolumeDOWN and Mute cause system to stop responding (apparently the system is stuck in a keyboard input loop or something).
2. Not using the Dell keys but mouse clicking also does not give any sound.

ALSAmixer shows all playback levels at max. Had checked that before, when running through this post:
[[ubuntu] [HOWTO] Fix for Stuck Volume/Multimedia Keys - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=974723") 

However, following this post I got still nowhere, functions keys still freeze the system and still no sound.

So I tried to follow the sound guide [http://fostergrant.ubuntuforums.org/showthread.php?t=205449](http://fostergrant.ubuntuforums.org/showthread.php?t=205449)

> 
ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

======

@ubuntu:~$ lspci -v

...
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
    Subsystem: Dell Device 0413
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at f0b00000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel


02:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]
    Subsystem: Dell Device 0413
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at cfeec000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
....



That is as far as I can get with this guide because I can't see to find the alsa driver for my hardware (or am I blind?)

The mic input seems to work because testing it makes the signal bars jump up. 

So shoot....:wink:

---

### Post by Glenn Louttit on 2010-04-01
Hi. I would like to add a few other matters. I have a Dell 1558 i5 processor and I am running Lucid Lynx. I have sound from time to time - it is there some days and others days it is not. There is no output through the earphone socket at all, but there is input from the microphone socket. Lucid lynx is fairly stable at this stage, but it ust has these issues that seem to change from day to day. 
Likewise the media player controls on the keyboard do not work and sieze up the whole operation i.e. unable to do anything until reboot. 
I am patiently waiting hoping that when the final version of Lucid Lynx comes out all these issues will be resolved.

---

### Post by venkidwaraka on 2010-05-21
@Glenn
You wont get a version with which all the problems will be solved. The problems keep on arising as we use it and patches will be released for that for each problem.

I also have the same model of Dell with ubuntu 10.04 and I dont face any media player issues. Please update the kernel and then try. That may fix it.

For the sound problem in using headphones I have got a solution from the ubuntu support group.Please visit the following link and perform the steps given and it will fix the problem
[https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

Thanks,
Venk!!

---

