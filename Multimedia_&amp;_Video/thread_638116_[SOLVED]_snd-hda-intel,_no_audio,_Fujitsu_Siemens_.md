---
title: "[SOLVED] snd-hda-intel, no audio, Fujitsu Siemens Lifebook  C1410"
date: 2007-12-11
forum: Multimedia &amp; Video
---

### Post by bracc0 on 2007-12-11
I finally got sound on my laptop!

I am with Ubuntu since version 6.10. I went thru 7.04 and I landed to 7.10. With all those version I hadn't any sound with my PC. I followed dozen of threads, I upgraded my ALSA stuff at least 20 times, I loaded and unloaded snd-hda-intel module from my kernel(s) without any success.

Now I have sound with my PC. The trick was in the kernel release.
I downloaded the vanilla kernel 2.6.23 and I applied the patch 2.6.24-rc4.
I compiled it starting from my Gutsy .config file. When dealing with the Sound tree, I enabled the snd-hda-intel module and (surprise!) I noticed that there is a sub menu under it! This is probably the stuff that did the trick.

I apologize for writing so quickly, but I am very happy for the sound and I want to share my happyness.
I can give further details upon request.

Thanks very much to everyone that contribute to these forums
Claudio
:guitar:

---

