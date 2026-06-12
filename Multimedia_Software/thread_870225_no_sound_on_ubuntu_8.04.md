---
title: "no sound on ubuntu 8.04"
date: 2008-07-25
forum: Multimedia Software
---

### Post by isr.igo on 2008-07-25
hi,

i have recently installed the ubuntu hardy X64  but i get no sound 
on an amd x64

but it finds the record

igor@igor-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

igor@igor-desktop:~$ sudo apt-get install linux-ubuntu-modules-$(uname -r)
[sudo] password for igor: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-ubuntu-modules-2.6.24-19-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

igor@igor-desktop:~$ lspci | grep audio
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)


any idea ??

---

