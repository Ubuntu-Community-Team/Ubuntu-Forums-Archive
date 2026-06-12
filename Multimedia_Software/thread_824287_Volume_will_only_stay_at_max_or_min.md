---
title: "Volume will only stay at max or min"
date: 2008-06-09
forum: Multimedia Software
---

### Post by foamingseizure on 2008-06-09
Hello, I'm an ubuntu newbie, so please bear with me.


I have on board sound. In Hardy, whenever I change my volume settings, it will only stay at the maximum or minimum. If I try to set it to any intermediate settings, the slider jumps to the maximum automatically. This occurs only on the default setting, "Realtek ALC660 (OSS Mixer)"

When I change the device to "Playback: ALSA PCM on front:0 (ALC861 Analog) via DMA (PulseAudio Mixer)", I can control the volume for most programs, but occasionally I'll open something and it'll blast me with maxed out sound.

Any help would be appreciated!

Here are some commands from another topic that may or may not be helpful:

*cat /proc/asound/version:*
Advanced Linux Sound Architecture Driver Version 1.0.16.
Compiled on May 29 2008 for kernel 2.6.24-18-generic (SMP).

*lspci:*
04:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)

*cat /proc/asound/card0/codec#0:*
Codec: Realtek ALC660

*aplay -l:*
**** List of PLAYBACK Hardware Devices ****
card 0: VT82xx [HDA VIA VT82xx], device 0: ALC861 Analog [ALC861 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: VT82xx [HDA VIA VT82xx], device 1: ALC861 Digital [ALC861 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

*At the bottom of my /etc/modprobe.d/alsa-base file is:*
options snd-cmipci mpu_port=0x330 fm_port=0x388


I hope that helps. If you need anything else, just ask. Thanks in advance!

---

### Post by foamingseizure on 2008-06-10
This may or may not be a related problem, but sometimes now no sound at all will come from my speakers when it should, and then out of nowhere all the sounds will come out at once.

I've looked through this forum, and can't find anything similar to the problem I'm having. Can anybody help me? :confused:

---

### Post by ginjabunny on 2008-06-11
I have had this on my laptop, the master volume is either max or off with nothing in between, but the other sliders work ok.

I have spent many hours trying different options in the /etc/modprobe.d/alsa-base and rebooting but nothing seemed to work properly, just certain bits worked, there is a list here to try, see [http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

Today I found a solution to my problems which reinstalls the alsa drivers and it seems to detect the sound card properly, if you try this and it doesn't work then I don't know how you undo it so beware, see my entry in [http://ubuntuforums.org/showthread.php?t=765867](http://ubuntuforums.org/showthread.php?t=765867) 

hope this helps :)

---

