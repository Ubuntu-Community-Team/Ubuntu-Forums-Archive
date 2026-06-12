---
title: "Surround 5.1 help"
date: 2008-09-15
forum: Multimedia Software
---

### Post by xmagixx on 2008-09-15
hej 
my surround is not playing to the right channels
allthough when i go to gnome mixer it's the right channel i adjust
the speaker-test also plays to the wrong channels
```
speaker-test 1.0.15

Playback device is plug:surround51
Stream parameters are 48000Hz, S16_LE, 6 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 5440
Period size range from 32 to 2720
Using max buffer size 5440
Periods = 4
was set period_size = 1088
was set buffer_size = 5440
0 - Front Left       OK
4 - Center           Should be Rear-Left
1 - Front Right      OK
3 - Rear Right       LFE
2 - Rear Left        Center
5 - LFE              should be Rear-Right

```
if i just swap the cables the sound gets all weird when i hear music , movies
how ever i can't enable surround on any dvd's it jsut play on all speakers and no surround
suggestions idéas ?

---

### Post by xmagixx on 2008-09-15
please do tell if you need any other information
rather new to GNU/Linux, so any help would be appreciated

from lspci
```
00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)

```

---

### Post by xmagixx on 2008-09-16
shameless bump

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

---

### Post by xmagixx on 2008-09-16
anyone know ? 
i think that in the alsa configuration i should swap the channels output
or in the gnome-alsamixer perhaps so the channels are what they say they are
but dont know how it can be done
meaby also in pulseaudio configuration
someone help me with this
how can i swap center/lfe with RR/RL channel

---

### Post by markbuntu on 2008-09-16
For the ALC 883 you need to look at this thread:

[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

---

