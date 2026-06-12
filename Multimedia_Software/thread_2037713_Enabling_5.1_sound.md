---
title: "Enabling 5.1 sound"
date: 2012-08-05
forum: Multimedia Software
---

### Post by Zvlwab on 2012-08-05
I bought a 5.1 surround set and connected it to my pc. Now when I play a sound, I do get sound from all speakers, but it's not surround.
changed the following line in /etc/pulse/daemon.conf
```
; default-sample-channels = 2
```
to
```
default-sample-channels = 6
```
And resetted my computer.
When I run a speaker test, I get the following results:
```
@pc:~$ speaker-test -Dplug:surround51 -c6 -l1 -twav

speaker-test 1.0.25

Playback device is plug:surround51
Stream parameters are 48000Hz, S16_LE, 6 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 22 to 5461
Period size range from 11 to 2730
Using max buffer size 5460
Periods = 4
was set period_size = 1365
was set buffer_size = 5460
 0 - Front Left          Works
 4 - Center
 1 - Front Right         Works
 3 - Rear Right
 2 - Rear Left
 5 - LFE
Time per period = 8.563897
```

---

### Post by Zvlwab on 2012-08-08
For some reason it just works now.

---

