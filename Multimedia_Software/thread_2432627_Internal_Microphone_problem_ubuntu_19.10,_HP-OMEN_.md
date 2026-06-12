---
title: "Internal Microphone problem ubuntu 19.10, HP-OMEN 17t-cb000"
date: 2019-12-05
forum: Multimedia Software
---

### Post by s-n on 2019-12-05
The built-in microphone for the laptop does not work
[ATTACH=CONFIG]284570[/ATTACH]

i write to /etc/modprobe.d/alsa-base.conf
**options snd_hda_intel model=auto**
pavucontrol   
[ATTACH=CONFIG]284569[/ATTACH]

**cat /proc/asound/card0/codec* | grep Codec**
Codec: Realtek ALC285 

**aplay -l**
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC285 Analog [ALC285 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by gnusci on 2019-12-05
Could you please post the output of:

$ lspci -v | grep -i audio

Thansk,

---

### Post by s-n on 2019-12-06
$ lspci -v | grep -i audio
00:1f.3 Multimedia audio controller: Intel Corporation Cannon Lake PCH cAVS (rev 10)
01:00.1 Audio device: NVIDIA Corporation Device 10f8 (rev a1)

---

### Post by gnusci on 2019-12-08
Did you check the mic in alsamixer?

---

