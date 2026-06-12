---
title: "No sound on Notebook Asus F3Jm with Intel 82801G"
date: 2006-10-25
forum: Multimedia &amp; Video
---

### Post by Jimmyqwy on 2006-10-25
I tried several different kernels and different ALSA versions, namely 1.0.12 and 1.0.13. But with all of them, the speakers stay silent.
My sound card is **HDA-Intel (High defination audio) - ALC861**
Does anyone have any suggestion?

---

### Post by LarsBjerregaard on 2006-11-10
Sound worked for me in Ubuntu Breezy, but in a completely new install of Dapper - no sound at all.
I see many people all over the place struggling with this. After many hours of googling, I found a simple workaround which works for me. It was described on: [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2038](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2038)

See also: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

So basically what I did (as root or using sudo):

1) Add to the bottom of /etc/modprobe.d/alsa-base:
options snd-hda-intel model=ref

2) Reboot

Voila! Sound works.

My system:

Dell Dimension 9150

OS: Ubuntu Dapper (6.06 LTS)

cat /proc/asound/version:
Advanced Linux Sound Architecture Driver Version 1.0.10rc3 (Mon Nov 07 13:30:21 2005 UTC).

lspci -vv | fgrep Audio:
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

cat /proc/asound/card0/codec#0:
Codec: SigmaTel STAC9221 A1

aplay -l:
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by Buggin on 2006-12-26
If I recall correctly that model has a fairly well known flaw where the button that detects headphones gets stuck

when you plug in headphones the button turns off your speakers and when it gets stuck they never turn back on

you can either fiddle around and unstick it or send it back to asus

---

### Post by skoalman88 on 2007-07-24
1) Add to the bottom of /etc/modprobe.d/alsa-base:
options snd-hda-intel model=ref

2) Reboot


ALSO WORKS IN FEISTY

---

### Post by zhinker on 2007-09-13
Beautiful, worked like a charm!

---

