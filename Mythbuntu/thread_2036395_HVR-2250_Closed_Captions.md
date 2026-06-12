---
title: "HVR-2250 Closed Captions?"
date: 2012-08-01
forum: Mythbuntu
---

### Post by Mad_Professor on 2012-08-01
Anyone got this card and got Closed Captions working on the analog side?

It showed /dev/video0 and 1 and also /dev/vbi0 and 1 but I can't use V4L Software encoder, because...
 10.04 black screen, stuck in loop
10.10 driver won't compile 
11.04 not able to test, distro severely buggy, kept crashing didn't setup mythtv even burn and iso was good. 
11.10 didn't test
12.04 same as 10.04 except it drops back to menu.

If I use IVTV or if you're using the newer 0.25 it's known as MPEG-2 Encoder
10.04 works but no Closed Captions
10.10 driver won't compile
11.04 buggy distro
11.10 didn't test
12.04 works, but can't change channels, drops out with random error on channel change, no closed captions but has an option for vbi device under Mpeg-2 encoder device.

So the question is can it display closed captions on 10.04 or 12.04?
if so, how is it setup on your end, how did you get it to work?

Would love to get card working..

---

### Post by nickrout on 2012-08-04
> **Mad_Professor said:**
> Anyone got this card and got Closed Captions working on the analog side?

It showed /dev/video0 and 1 and also /dev/vbi0 and 1 but I can't use V4L Software encoder, because...
 10.04 black screen, stuck in loop
10.10 driver won't compile 
11.04 not able to test, distro severely buggy, kept crashing didn't setup mythtv even burn and iso was good. 
11.10 didn't test
12.04 same as 10.04 except it drops back to menu.

If I use IVTV or if you're using the newer 0.25 it's known as MPEG-2 Encoder
10.04 works but no Closed Captions
10.10 driver won't compile
11.04 buggy distro
11.10 didn't test
12.04 works, but can't change channels, drops out with random error on channel change, no closed captions but has an option for vbi device under Mpeg-2 encoder device.

So the question is can it display closed captions on 10.04 or 12.04?
if so, how is it setup on your end, how did you get it to work?

Would love to get card working..

I don't know the answer to your question about closed captions, but this card is an mpeg2 encoder, you can't use it as a V4L encoder in mythtv. However you should probably run mythfrontend with -v vbi to get some clues.

---

