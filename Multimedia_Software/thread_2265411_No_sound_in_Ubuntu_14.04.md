---
title: "No sound in Ubuntu 14.04"
date: 2015-02-14
forum: Multimedia Software
---

### Post by alex331 on 2015-02-14
I upgrade to 14.04  from 12.04 and I have no sound in my PC

I checked the system setting->sound and tested there and no sound . In the current kernel version no HDMI card is showen in the system setting->sound

The alsa script give this output


[http://www.alsa-project.org/db/?f=fef277c0c0768cc3a0ff4d07e88ca39be9e3fc1e](http://www.alsa-project.org/db/?f=fef277c0c0768cc3a0ff4d07e88ca39be9e3fc1e)

I tried different task to solve this issue (reinstall pulseaudo, alsa, add hdmi to kernel througth parameter, modified asound.conf, etc). I hope didn't break more the system.

As you will see in the link I have:
$ lspci|grep -i audio
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) (rev 40)
01:05.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] RS880 HDMI Audio [Radeon HD 4200 Series]
$ 

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
$ 


Thanks in advance

---

### Post by alex331 on 2015-02-15
Sorry, I couldn't wait. I reinstall Ubuntu 12.04.5 and I have sound again

---

