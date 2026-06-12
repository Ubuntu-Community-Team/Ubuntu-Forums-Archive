---
title: "alsa works in terminal, does not work under X"
date: 2012-12-03
forum: Multimedia Software
---

### Post by svrkispm on 2012-12-03
Hello,
I have Ubuntu 12.04.1, it's a very minimalistic system, it has only alsa and fluxbox (I don't have pulseaudio or other fancy stuff).

My problem is, that sound works only in console (by console I mean /dev/ttyX), when I try it in terminal under X, it does not work.

in console:
```

aplay -l
card 0: Intel [HDA Intel], device 0: ALC269VB Analog ...
...
card 0: Intel [HDA Intel], device 3: HDMI 0 ...
...

```

```

aplay sound.wav
Playing WAVE 'sound.wav' : Signed 16 bit Little Endian ...

```

in terminal under Fluxbox:
```

aplay -l
aplay: device_list:252: no soundcards found...

```

```

aplay sound.wav
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
...

```

I haven't pasted the exact text in here, if it is needed I can try to. I don't have net connection there yet :)
Thanks for your advices.

--update--
while i was trying to document this i tried to check group membership. After adding user to groups audio and pulse-access it now works fine.

---

