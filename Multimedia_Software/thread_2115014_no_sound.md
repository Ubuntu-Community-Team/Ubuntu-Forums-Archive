---
title: "no sound"
date: 2013-02-11
forum: Multimedia Software
---

### Post by zhanfei on 2013-02-11
I checked my ubuntu version by the following way:
lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.2 LTS
Release:    12.04
Codename:    precise

At the beginning, my problem the front speaker and the headphone work together, even after I plug in the headphone. Then I followed some advices on the web and closed the "front" in alsamixer. Then I found I have sound at all. Even opening the "front" now can't help. Does anyone know what is going on here? Thanks:)

---

### Post by Yellow Pasque on 2013-02-11
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by zhanfei on 2013-02-12
Here is my alsa-info:

[http://www.alsa-project.org/db/?f=952754d014f8d15541c47b4336fccc3e8455b269](http://www.alsa-project.org/db/?f=952754d014f8d15541c47b4336fccc3e8455b269)

---

### Post by zhanfei on 2013-02-12
Now I have got the sound back by choosing "play sound through analogue output" in "sound settings". Probably I clicked "play sound through digital output" and it doesn't work, I guess. But the original problem is still not solved:  Sound comes from the front speaker even after I plug in the headphone. Anyone has an idea about this?

---

### Post by Yellow Pasque on 2013-02-12
Other people with that laptop have the same issue. [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1004931](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1004931)

---

### Post by zhanfei on 2013-02-15
> **Temüjin said:**
> Other people with that laptop have the same issue. [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1004931](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1004931)

So no solution so far?

---

