---
title: "Recording screencasts with sound coming from another program's ALSA output"
date: 2008-03-06
forum: Multimedia &amp; Video
---

### Post by ivucica on 2008-03-06
Cheers,

I'm in need of a screencasting tool that can record the sound output of a certain application (or of entire desktop) instead of recording the microphone. Recordmydesktop is perfectly suited for my needs except it records the microphone, not my desktop output.

In Windows (yuck) it's easy to switch recording "input" to the actual "output" of the sound mixer. Is there any way to make a new ALSA input (recording) device which would actually just pipe out the contents of an ALSA output device?

I can't do the ugly hardware-based method involving plugging output in line-in, since I literally don't have line-in on a laptop and I doubt that plugging it into a microphone jack would work. Besides I'd "lose quality" in the A->D->A conversion which is hopefully unneeded.


I'm watching for responses
:popcorn:

---

### Post by ivucica on 2008-04-15
For my purpose of recording sounds from my game which is coded with SDL, I can use SDL_AUDIODRIVER=disk. But that's still not what I originally wanted; if someone can make output from any ALSA program (including xmms, and even daemons such as esd and artsd) get recorded, please poke me.

I'll watch carefully.

---

