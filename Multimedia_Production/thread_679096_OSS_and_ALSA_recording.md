---
title: "OSS and ALSA recording"
date: 2008-01-26
forum: Multimedia Production
---

### Post by cinajohn on 2008-01-26
I am trying to get my new M-Audio Delta Series Audacity 192 working.  Not sure if this was the right move but I switched to OSS.  All playback is working fine but I am having trouble recording.  The OSS mixer shows signal on the input, but 'sound recorder' records completely distorted and since switching to OSS audacity crashes when I ask it to record or even monitor.   

So...
a)how can I get this setup to work?  ...or...
b)shall I just try with ALSA instead?

Thanks

---

### Post by chipants on 2008-02-19
just use alsa instead. the audiophile 192 should work just fine. out of curiosity, why did you switch to OSS? it really isn't very cutting edge; and, most modern linux professional audio applications use alsa+jack.

---

### Post by kayosiii on 2008-02-20
The most recent version of Audacity I think supports Jack... you could try getting Jack setup - admittedly not as trivial as it should be... But Jack is pretty much where you want to be for pro audio on linux anyways.

---

### Post by chipants on 2008-02-22
> **kayosiii said:**
> The most recent version of Audacity I think supports Jack... you could try getting Jack setup - admittedly not as trivial as it should be... But Jack is pretty much where you want to be for pro audio on linux anyways.

audacity has supported jack for quite a long time, actually. however, i'm not sure i understand what that's got to do with this thread. :) jack is actually relatively easy to set up.

simply install jack, and preferably qjackctl from the repository. defaults within qjackctl should provide a functional (if not optimally performing) jack setup for most people. and if for some reason the defaults keep jack from running, there are sooo many people to help.

---

