---
title: "Sound doesn't work"
date: 2012-02-19
forum: Multimedia Software
---

### Post by eduardops2 on 2012-02-19
id hate hijack this thread but i cant figure out how to post on this site 

i have a sound problem to i have checked alsa mixer and its all good but i get no sound from my headphone jack 

pc info> ==> /proc/asound/card1/codec#0 <==
Codec: ATI RS690/780 HDMI
djmonkay@Djmbox-m1:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.24.
djmonkay@Djmbox-m1:~$ uname -a
Linux Djmbox-m1 3.0.0-16-generic #28-Ubuntu SMP Fri Jan 27 17:44:39 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
djmonkay@Djmbox-m1:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: SB [HDA ATI SB], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
djmonkay@Djmbox-m1:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.24.
djmonkay@Djmbox-m1:~$ 


---

### Post by oldos2er on 2012-02-20
Post moved to its own thread.

---

