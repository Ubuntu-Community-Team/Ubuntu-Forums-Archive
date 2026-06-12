---
title: "No sound with Toshiba Satellite P105"
date: 2014-01-20
forum: Multimedia Software
---

### Post by walterdowis on 2014-01-20
Hi All,
    I'm new to Linux and Ubuntu.  I installed Ubuntu on an old Toshiba Satellite P105, Celeron M, Model Number PSPA0U-1EN032.  
    I'm not getting sound.  I was hoping someone with this type of computer could help me restore the sound. 
    Everything else on the computer is woking fine such as wifi, video, printer, etc.  It's only the sound that's missing. 
    Thanks.

---

### Post by Yellow Pasque on 2014-01-21
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by walterdowis on 2014-01-21
Hi Temujin,
    I followed the script and got this link.  Thanks for you help.  
     [http://www.alsa-project.org/db/?f=623335a6c7c6b1016fcb374e0bc98f70226b29dc](http://www.alsa-project.org/db/?f=623335a6c7c6b1016fcb374e0bc98f70226b29dc)

---

### Post by walterdowis on 2014-01-21
Here is some more information. I entered this command in the command line terminal:  
cat /proc/asound/card0/codec* | grep Codec
 
I got this result: 
 
Codec: conexant cx20551 (waikiki)
 
Hopefully this information will help.

---

### Post by Yellow Pasque on 2014-01-22
It looks like a longstanding bug: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/847071](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/847071)

---

