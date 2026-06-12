---
title: "Sound buttons and controls in Ubuntu works but volume never changes"
date: 2007-11-25
forum: Multimedia &amp; Video
---

### Post by niche25 on 2007-11-25
Hey guys,

I recently installed Ubuntu 7 on my laptop and almost everything works great. The one big problem I have is the volume. If I press the volume buttons up or down on the laptop it shows it changing on my screen but the volume itself never actually changes. The same thing applies when I change the volume within the Ubuntu volume controls - I am not sure what I need to do here and I would really appreciate the advice.

Currently the volume is always very loud and when I turn the computer on it screams Ubuntu (which isn't a problem, I love advertising Linux and this awesome OS but I also tend to wake my children up and my wife is starting to get pissed... LOL).

Thanks guys!!

---

### Post by human-ness on 2007-11-26
You may be running ALSA as your engine so to speak, but OSS mixer as your steering wheel.  If this is the case, when you change your volume, nothing happens, because your steering wheel doesn't fit the engine.

In your top menu of your mixer, have a look if OSS is selected as the mixer.  If it is, flick it over to ALSA.  Or vice versa, if it happens to be on ALSA already.  See how that goes.

---

### Post by eewestcoaster on 2008-02-18
I'm having the same problem on my Dell XPS Gen2 - everything works but the sound controls.  

I was running the ALSA mixer, so switched it over to the OSS.  No change.  Okay, that's not true - the parameters I had access to on the mixer table changed (PCM / PCM-2, etc), but the functionality doesn't change.

The buttons on the front of the laptop seem to control the main laptop speakers, while the OS still controls an internal speaker of some sort.  It's very strange.

It looks like I'm not the only one having this issue - has it been resolved yet?

---

### Post by mrb88 on 2008-04-28
Had this problem with my Dell XPS M170. The fix is [http://ubuntuforums.org/showthread.php?t=128002](http://ubuntuforums.org/showthread.php?t=128002)

Just set it to PCM instead of Master or Master Mono and adjust Master Mono (your subwoofer) to what sounds good when Master is at max.

---

