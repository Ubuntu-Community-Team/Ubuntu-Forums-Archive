---
title: "Sound Card doesn't sound."
date: 2007-12-13
forum: Multimedia &amp; Video
---

### Post by rolodoom on 2007-12-13
Hello. I just notice that my card stops working. I have a Sound Blaster Live 5.1.
I have tested the next way so I think that the card is still correctly installed, so I guess the problem is somewhere I don't know. 

MyCard:

```

rolodoom@rolinux:~$ cat /proc/asound/cards
 0 [Live           ]: EMU10K1 - SB Live [Unknown]
                      SB Live [Unknown] (rev.10, serial:0x80671102) at 0x1000, irq 21

```
Then I tested with the next command and actually get sound, but only from console, when I open totem, audacity, etc, there is no sound. Jack also stops working.

```

rolodoom@rolinux:~$ speaker-test -Dplug:surround51 -c6 -twav

speaker-test 1.0.14

Playback device is plug:surround51
Stream parameters are 48000Hz, S16_LE, 6 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 16384
Period size range from 16 to 16384
Using max buffer size 16384
Periods = 4
was set period_size = 4096
was set buffer_size = 16384
 0 - Front Left
 4 - Center
 1 - Front Right
 3 - Rear Right
 2 - Rear Left

```
Where is the problem??

---

