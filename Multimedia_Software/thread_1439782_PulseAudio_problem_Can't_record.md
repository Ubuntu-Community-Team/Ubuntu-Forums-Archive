---
title: "PulseAudio problem: Can't record"
date: 2010-03-26
forum: Multimedia Software
---

### Post by vace117 on 2010-03-26
Hello. I've just upgraded to Karmic and I am having some PulseAudio issues.

My first impulse was to remove Pulse right away and just go with ALSA, but I noticed that Pulse seems to be working pretty well for most things now, so I decided to give it a try.

I got everything working now, except for recording. It worked in the very beginning, but after I installed *pavucontrol* and *paman* and played with some settings, I can no longer figure out how to record.

I have three sound devices, according to GNOME's volume manager:
 - Internal Audio Analog Stereo
 - SAA7131/SAA7133/SAA7135Video Broadcast Decoder Analog Stereo
 - ICE1712 [Envy24] PCI Multi-Channel I/O Controller Digital Stereo (IEC958)

I have my microphone hooked up to an input on the ICE1712.

Recording from the Internal card works fine (with a different MIC I hooked up just for testing). What I need to do is tell Pulse that I want to record from the ICE1712 card, and I can't figure out how to do it.

I know that the underlying ALSA setup is correct, b/c this works:
```
arecord -f dat -Dplughw:1,0 test.wav
```

Also, Audacity can record directly from the ALSA device. In Pulse, however, selecting ICE1712 as the input produces no sound from the mic. 

These screenshots show my Pulse configuration and the state of sinks and sources in the Device Manager:
[http://i41.tinypic.com/25u2jw0.jpg](http://i41.tinypic.com/25u2jw0.jpg)
[http://i44.tinypic.com/2dv2wpf.jpg](http://i44.tinypic.com/2dv2wpf.jpg)

Just for reference, when recording from Internal, it looks like this:
[http://i44.tinypic.com/205v9th.jpg](http://i44.tinypic.com/205v9th.jpg)

So, it looks like the correct sources are being used...

Since it worked at first and since ALSA works fine, this is clearly possible to get working... Is this a Pulse bug, or am I missing something?

Any help would be greatly appreciated.


Val

---

