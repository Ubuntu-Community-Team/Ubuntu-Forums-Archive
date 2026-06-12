---
title: "Lubuntu 18.04. ALC668 Realtek no sound from headphones"
date: 2018-09-13
forum: Multimedia Software
---

### Post by hdaemon on 2018-09-13
No sound from headphones in Lubuntu 18.04. 
PLease Help.

---

### Post by Yellow Pasque on 2018-09-13
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by slickymaster on 2018-09-13
*Thread moved to **Multimedia Software**.*

---

### Post by hdaemon on 2018-09-14
> **Temüjin said:**
> [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)
[http://www.alsa-project.org/db/?f=a7bccede7ed0f28ab3f1762a06f9b64ea0417628](http://www.alsa-project.org/db/?f=a7bccede7ed0f28ab3f1762a06f9b64ea0417628)
 
In Kubuntu 18.04 on same machine all works perfect. Here you can get information about my previous system: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1790595](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1790595)

---

### Post by hdaemon on 2018-09-14
add options snd-hda-intel model=asus-mode5 to alsa-base.conf  as there [https://ubuntuforums.org/showthread.php?t=2300693](https://ubuntuforums.org/showthread.php?t=2300693) and now i hear some activity on statrtup in headphones. but still no sound output.

---

### Post by hdaemon on 2018-09-16
Strange things. If headphones with microphone, there is no sound, but if without microphone, sound is present.

---

### Post by hdaemon on 2018-09-17
Sorry just found this thread  [https://ubuntuforums.org/showthread.php?t=2312163](https://ubuntuforums.org/showthread.php?t=2312163) 
options snd-hda-intel model=dell-headset-multi
Solved.

---

