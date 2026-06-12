---
title: "4-speaker setup with ALSA (R L C +sub), no love"
date: 2010-11-09
forum: Multimedia Software
---

### Post by Aped on 2010-11-09
Basically, yeah. My center speaker isn't working at all and my sub appears to be working but only incidentally. 

Relatively new to setting up more-than-two speaker configs, so don't hate if I'm doing it wrong please. 

Anyway, the symptoms: Under "Sound Preferences..." from the drop-down menu in 10.10, I go to Hardware and then Test Speakers and while the front two (R and L) play just fine (and also cause the sub to play a bit) there is no center channel action at all and the sub's dedicated button does nothing. 

Things I've tried so far:
-added `options snd-hda-intel model=CMI8736-MC6` (my card according to its pci entry in lshw/lspci is a CM8738-MC6) to /etc/modprobe.d/alsa-base
-attempted to use `aplay -vv test.wav`
-attempted to do a `speaker-test -Dplug:surround51 -c4 -twav` (also tried with other flags besides surround51 and -c4, though my attempts were more random shots in the dark than exhaustive precision debugging)
-yelled at my computer, receiver, alsa webpage, television

Is there anything else I can yell at, ubuntuforums? Failing that, is there some sort of technical recourse that I can take? 

Thanks in advance (and as usual) for your time and assistance. If there's any salient information that I've left out, please feel free to mention it.

EDIT: SOLVED

---

