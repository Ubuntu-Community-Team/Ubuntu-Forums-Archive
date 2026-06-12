---
title: "MuseScore -&gt; Won't start, segfault."
date: 2010-06-15
forum: Multimedia Software
---

### Post by fn00dle on 2010-06-15
Hi, I'm using Ubuntu 10.04 with OSS as sound driver. I complete deinstalled ALSA and Pulse, and still, when I try to start MuseScore, I get this reply:
```
jonathan@jonathan:~$ mscore
PulseAudio found, but no need to suspend. Starting mscore.real...
Alsa_driver: the interface doesn't support mmap-based access.
init ALSA audio driver failed
init ALSA driver failed
Init midi driver failed
no audio output found
init audio driver failed
sequencer init failed
Segmentation fault
```

When I install alsa-oss and try to run it via aoss, I get:```
jonathan@jonathan:~$ aoss mscore
PulseAudio found, but no need to suspend. Starting mscore.real...
Alsa_driver: the interface doesn't support mmap-based access.
init ALSA audio driver failed
init ALSA driver failed
Init midi driver failed
no audio output found
init audio driver failed
sequencer init failed
Segmentation fault

```

Note: the splash screen appears for a split second, then closes.
Anyone who can help me with this? Using free windows software (Finale NotePad) under Wine does not work either and I really need to have a music notation program running for school assignments..

Thanks in advance!

---

### Post by fn00dle on 2010-06-20
Bump

---

