---
title: "Muffled sound using 10:04"
date: 2010-05-08
forum: Multimedia Software
---

### Post by Swagman on 2010-05-08
As per topic title, I have just clean installed Lucid 64 on a new mobo & hard drive but the sound output is abysmal.

Extremely muffled is the best description I can give. It's like turning the treble down to minus 5 !!

I'm using a Logitech 5.1 sound system. pressing the matrix button results in no sound whatsoever (oh noes... a glitch in the matrix).

Sound prefs show there are no 5.1 or other options as before in Karmic.

[img]http://www.upload3r.com/serve/080510/1273312240.jpeg[/img]


Anyone know how to cure this or an equaliser I can install please ?

---

### Post by Swagman on 2010-05-08
Bump

```

paul@pauls-desktop:~$ uname -a
Linux pauls-desktop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux
paul@pauls-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
paul@pauls-desktop:~$ 
paul@pauls-desktop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
paul@pauls-desktop:~$ head -n 1 /proc/asound/card*/codec#*
Codec: VIA ID 440

```

---

### Post by Swagman on 2010-05-08
Solved.

Swapped the jacks around at the back.

ie: Black in the green port & vice versa ??????????

Sorted (go figure)

---

