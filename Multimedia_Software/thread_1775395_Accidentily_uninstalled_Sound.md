---
title: "Accidentily uninstalled Sound"
date: 2011-06-04
forum: Multimedia Software
---

### Post by jeroenisblij on 2011-06-04
I am running Ubuntu 11.04 on a Mac Pro. Since the update from 10.10 to 11.04, apache was acting strange, and I could not figure out how to fix it. Therefore I decided to remove and purge all apache components and reinstall it. 

The good news is that Apache2 is working again. The bad news is that in the process, all software that depended on Apache2 was also removed. After restaring my computer, among others, printing and sound support had disappeared.

I managed to restore printing support by reinstalling CUPS. However I am not sure which package I should reinstall to get my sound back? The HW is still OK, but the volume button disabled:

jeroen@jeroen-ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: device [Apple USB audio device], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

