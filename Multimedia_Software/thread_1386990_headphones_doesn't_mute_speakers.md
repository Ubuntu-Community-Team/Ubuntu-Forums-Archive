---
title: "headphones doesn't mute speakers"
date: 2010-01-21
forum: Multimedia Software
---

### Post by .ringaila on 2010-01-21
Hello everybody,
I have ASUS F3Ka laptop. I have installed both Win7 & Ubuntu 9.10
unfortunately when I'm using Ubuntu the system doesn't recognize my headphones and plays the sound from speakers & headphones at the same time... This is an information of my sound card:

laptop:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC660-VD
Codec: Motorola Si3054
laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC660-VD Analog [ALC660-VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC660-VD Digital [ALC660-VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Any suggestions?
p.s. sorry for my English.

---

### Post by lidex on 2010-04-03
Try this. Open a terminal ("Applications>Accessories>Terminal). Enter this command:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
At the bottom of that file add this line:
```
options snd-hda-intel position_fix=1 model=lenovo
```
Save. Close. Reboot.

---

