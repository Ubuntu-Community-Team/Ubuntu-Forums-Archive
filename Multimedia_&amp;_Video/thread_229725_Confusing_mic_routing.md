---
title: "Confusing mic routing"
date: 2006-08-04
forum: Multimedia &amp; Video
---

### Post by christian.convey on 2006-08-04
I've got a laptop with a Centrino chipset and an Intel ICH6 audio controller.  I have a microphone plugged into the (physical) mic jack on the laptop. Can anyone explain the following to me?

Regardless of whether or not I have jackd running, I get the following behavior:
In alsamixer, if I have "Line Jack Sense" set to "off", I can hear the microphone's input sound mirrored out onto the laptop's speakers.  If it's set to "on", I hear nothing on the laptop's speakers.

The part I'm confused about is why there would be any kind of audio routing from the microphone to the laptop's speakers without me explicitely setting that up.  And, in the end, I want to be able to suppress it: the only way I want sound getting from my mic to my speakers is if it passes through jack-rack along the way.

Any suggestions/clues?

Thanks,
Christian

---

### Post by christian.convey on 2006-08-04
OK, I've somewhat figured it out.  My alsamixer has a setting called "Mic".  This is not an attenuation control for the mic input as I had supposed.  Instead it appears to control how strongly the mic's sound is directly copied to speakers.

So, setting this mixer value to zero (or muting it) fixed my problem.

---

