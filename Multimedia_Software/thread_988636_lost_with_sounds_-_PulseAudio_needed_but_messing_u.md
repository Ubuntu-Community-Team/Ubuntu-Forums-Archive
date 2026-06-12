---
title: "lost with sounds - PulseAudio needed but messing up things"
date: 2008-11-20
forum: Multimedia Software
---

### Post by zozio32 on 2008-11-20
Hi

I've just manage to get some sound back in my laptop, but still not good.
A small summary of what happen to my computer in the last few week:

1: when Intrepid got available. I download it and I've been happy with it for a few days, everything working (skype + music + sound in firefox all together)

2: my Nvidia card fried up, so I had a dell engineer changing my full motherboard (I have a laptop) --> since that day, no sound in ubuntu but was working in Vista (not a hardware problem)

3: in the pas few days, I've tried to re-install everything related to ALSA and PulseAudio without any success: no sound at all - just some cracking in the speaker when trying to play something.

4: I've removed completely pulseaudio, and magic, Rythmbox is happy playing music :).  But I still have no sound out of Firefox or Skype.
Tried to re-install pulseaudio

5: back to faint cracking sounds even with Rythmbox. Un-install and restart -> back to point 4.

So, I definitely have a problem with pulseaudio, but I need it for Skype, Firefox, etc.    Any solution?

---

### Post by zozio32 on 2008-11-21
any one for that problem, or even an other relevant thread to point out?
I've done a research but I haven't found something specific enough, surely because I don't ave much expertise in this domain

---

### Post by psyke83 on 2008-11-21
Intrepid has a bug where the PCM mixer gets muted/set to 0%. Make sure that's not the case for you:
```
$ alsamixer -Dhw
```

Also see the [PulseAudio Fixes]("http://ubuntuforums.org/showthread.php?t=789578") guide.

---

