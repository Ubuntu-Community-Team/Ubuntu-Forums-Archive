---
title: "Need audio setting changes"
date: 2010-04-16
forum: Multimedia Software
---

### Post by sskrajak on 2010-04-16
Hi friends,
                 I have 5 channel speakers. but the sound come only from 2 speaker, even though the audio is 2 channel. 
                how to enable it ?
                I am having ubuntu 9.10 version installed. My system can play 5 channels.
 
Regards
sskrajak

---

### Post by lidex on 2010-04-18
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

