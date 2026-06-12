---
title: "Toshiba Satellite U300 ( intel hda ALC268 ) microphone problem"
date: 2018-04-29
forum: Multimedia Software
---

### Post by vulcanero on 2018-04-29
Good day, friends. I have  permanent problem with microphone on my laptop with ubuntu 16.04 i386
I've try to insert many different strings like "options snd-hda-intel model= "      in  /etc/modprobe.d/alsa-base.conf but have no changes
 microphone volume is very low. if I increase the level of the regulator, the indicator shows overload. microphone sound is still quiet and distorted
if I record in audacity, I can see that the microphone graph is shifted, as if it is fed phantom power
Both microphones internal and external have this problem
Windows is OK
Please help

---

### Post by mörgæs on 2018-04-30
People who know about sound often want this information from you:
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by vulcanero on 2018-05-01
pcilib: sysfs_read_vpd: read failed: Input/output error
Automatically upload ALSA information to [www.alsa-project.org?](www.alsa-project.org?) [y/N] : y
Uploading information to [www.alsa-project.org](www.alsa-project.org) ...  Done!

Your ALSA information is located at [http://www.alsa-project.org/db/?f=21de64d0a88c057cdd9ecb7085b95a92f4c96b1d](http://www.alsa-project.org/db/?f=21de64d0a88c057cdd9ecb7085b95a92f4c96b1d)

Please inform the person helping you.

---

### Post by vulcanero on 2018-05-12
anyone have ideas ? problem still actual  :(

---

