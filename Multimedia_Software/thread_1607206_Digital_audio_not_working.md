---
title: "Digital audio not working"
date: 2010-10-27
forum: Multimedia Software
---

### Post by cruncee on 2010-10-27
Hey guys,

I just installed Ubuntu 10.10.

Can someone help me to get the digital output of my soundcard working?


```
xxx@xxx:~$ uname -a
Linux xxx 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:36:48 UTC 2010 i686 GNU/Linux
xxx@x:~$ aplay -l
**** Liste der Hardware-Geräte (PLAYBACK) ****
Karte 0: Intel [HDA Intel], Gerät 0: ALC889A Analog [ALC889A Analog]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 0: Intel [HDA Intel], Gerät 1: ALC889A Digital [ALC889A Digital]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
xxx@xxx:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
xxx@xxx:~$ head -n 1 /proc/asound/card*/codec#*
Codec: Realtek ALC889A
xxx@xxx:~$ 


```

Thank you guys!

Cruncee

---

