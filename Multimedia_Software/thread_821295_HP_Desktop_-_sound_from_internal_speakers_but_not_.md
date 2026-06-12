---
title: "HP Desktop - sound from internal speakers but not headphones"
date: 2008-06-07
forum: Multimedia Software
---

### Post by Bonez56 on 2008-06-07
Hi all,

I have a HP D530S desktop PC with Ubuntu 8.04 Hardy x86 installed.

The PC has internal speakers. They are working, but if I try to plug in a pair of headphones, or plug a cable from the headphone output into my home hifi system, I can not get any external sound.

I have checked to make sure that all of the mixers are unmuted, and am using Alsa.

Here's some more details:

```
~$ lspci |grep -i audio
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)

```

```

matt@earth:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
matt@earth:~$ 

```

Can anyone please assist here? Am I missing something or is there a bug with this soundcard in Ubuntu?

Thanks
Bonez56

---

### Post by Pjotr123 on 2008-06-07
Check this page:
[http://ubuntutip.googlepages.com/sound](http://ubuntutip.googlepages.com/sound)

---

### Post by kwas101 on 2009-02-15
I have the same problem, plenty of sound from the internal speaker and none from external ones. I even went into the BIOS and disabled "Intel Audio" yet still I get sound from the internal speaker...why why??

aplay - l gives me:
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: pcsp [pcsp], device 0: pcspeaker [pcsp]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I guess it must have something to do with card 1 (the pc speaker) but perhaps not. I can run alsamixer on either card 0 or card 1. 

I would really like to get some lovely sound out of my external (stereo) speakers. Thanks all :-)

---

