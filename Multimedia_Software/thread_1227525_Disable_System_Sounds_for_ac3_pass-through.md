---
title: "Disable System Sounds for ac3 pass-through"
date: 2009-07-30
forum: Multimedia Software
---

### Post by dehip on 2009-07-30
Hi,

I recently upgraded to jaunty and have some problems with mplayer ac3 passthrough which I think are _not_ related to general pulse issues. Context follows below, but the main question is:

In the pulse audio volume control something called "System Sounds; Mono" appeared which I can not seem to kill. Which program causes this and how do I kill it?
In the System>Preferences>Sound>Sound-tab I have 'Play sound and sound effects' turned off (always had, always will).

In 8.10, after a lot of tinkering and following guides, I got pulse audio to work, while still being able to use the mplayer pass-through [-ao alsa -afm hwac3] for my sp/dif cable (and separate usb headphones concurrently, yeah!).
After the upgrade, everything worked a bit buggy so I did the config clean-up suggested in one of the sticky threads. Now pulse works like a charm (apart from the occasional cracking sounds), auto-detecting the digital output and everything, but ac3 pass-through doesn't give any sound anymore.

When I play a movie, there are no error messages, and the amp actually blinks that it is receiving DTS/AC3, but there is no sound. (Software decoding to stereo works, in stereo..)
For completeness, pulseaudio does give the "...not in group 'pulse-rt', PolicyKit..." error, but that's not really a problem for anything as far as I can see.

What I remembered from the functional setup in 8.10 is that I had to make sure that 1) all mixer channels (from alsa) need to be turned up to maximum, and 2) no other programs were causing sounds (easily verified by looking at the pulse audio volume control). Otherwise I guess some mixing would still occur breaking the signal sent.

This leads me to think that the System Sounds displayed in the pulse audio volume control breaks the ac3 signal. I might be wrong though, but it is the next thing on my list to try, but I can't figure out how to remove these System Sounds. I did manually kill a lot of programs with all sorts of funny results, but none of them restored my audio .)

Regards

P.S. First post and all, so please forgive any wrongdoings .)

---

