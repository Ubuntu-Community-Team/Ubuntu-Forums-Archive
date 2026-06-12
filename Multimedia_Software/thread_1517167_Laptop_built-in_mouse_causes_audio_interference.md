---
title: "Laptop built-in mouse causes audio interference"
date: 2010-06-24
forum: Multimedia Software
---

### Post by heggink on 2010-06-24
I recently reimaged an old HP nc4000 with lucid. Everything works like a charm except for one little thing: when playing sounds, using the built-in mouse causes interference with the audio. No mouse movement == no interference. Also, connecting an external mouse does not cause interference. Seems like the mouse driver events interfere with the audio in some way. sound module used is snd_ali5451. Mouse is a synaptics mouse pad. using gstreamer-properties, i tried every possible plugin with no difference: all plugins have the same issue.

Help greatly appreciated.

Herman

---

### Post by ajgreeny on 2010-06-24
Does this laptop have a microphone that is picking up the noise of your finger sliding across the trackpad and then the sound is amplified?

You could always try ```
alsamixer
``` in terminal and make sure the microphone is muted.  If that is not the problem, then I can not imagine where else you could look.

---

### Post by heggink on 2010-06-25
I muted everything i could possibly mute (channels, Mic's). Uninstalled pulse but the problem persists. The laptop ran XP before with no issues. The sound is some kind of weird digital interference as it's very consistent in the type of noise it makes. Tried to figure out if it could have something to do with internal conflicts (e.g. IRQ) that could cause the sound to be impacted. Also, when no music plays, there is no sound so it inly interferes and does not generate noise itself. Googling for this, i saw many cases of static interference but all of them generated noise themselves, not impacted existing sound...

---

