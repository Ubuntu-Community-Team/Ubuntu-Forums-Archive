---
title: "Rear and Centre Speakers not working"
date: 2012-05-20
forum: Multimedia Software
---

### Post by SPARTAN-118 on 2012-05-20
After installing a new motherboard (ASRock N68C-S UCC), I booted into Ubuntu to discover that the front two speakers work, but it seems as if the mobo is not detecting the other two jacks as outputs, even if I specify as such in Sound Settings. So that translates to my 5.1 Logitech X-540 system becoming a 2.1 Logitech system. Suggestions? I tried running ```
speaker-test -c6 -l1 -twav
``` and it did the whole run-through, here's the output, though I'm not sure how much help it'll be:
```
$ speaker-test -c6 -l1 -twav
speaker-test 1.0.25

Playback device is default
Stream parameters are 48000Hz, S16_LE, 6 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 32 to 349525
Period size range from 10 to 116509
Using max buffer size 349524
Periods = 4
was set period_size = 87381
was set buffer_size = 349524
 0 - Front Left
 4 - Center
 1 - Front Right
 3 - Rear Right
 2 - Rear Left
 5 - LFE
Time per period = 9.438920

```
Only 0 and 1 actually output anything. As I said, it's like the mobo doesn't recognize the mic and line in ports as 5.1 outputs, even when Ubuntu does.

---

