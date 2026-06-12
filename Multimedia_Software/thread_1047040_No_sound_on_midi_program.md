---
title: "No sound on midi program"
date: 2009-01-22
forum: Multimedia Software
---

### Post by tegnoto89 on 2009-01-22
I'm trying to use a Finale-type music program called Nted, and I can't hear any sound.  Here's what the documentation gives me:



Your failure to hear sound has nothing to do with NtEd! It is a problem of your MIDI device! All MIDI based applications
(for instance kmid (not kmidi !!!) or pmidi) will fail!

First of all: Try to play a MIDI file with kmid (not (!!!)
kmidi). As long as kmid does not produce any sound, NtEd
(and any other MIDI device based software) will not produce any sound, too!
The reason is: Either your soundcard has no hardware MIDI synthesizer or
it has a hardware MIDI synthesizer but it is not supported by Linux.






Any suggestions?  How do I figure out what my sound card is and whether or not it's supported?  I was able to play finale midi files on windows..

---

### Post by markbuntu on 2009-01-22
lspci will give you a list of hardware including the sound card/chip
aplay -l will tell you what driver is being used

Windows will use a software midi emulator automatically if midi hardware is not available. The vast majority of sound hardware on pcs these days does not have midi hardware and there are even fewer with midi driver support so an emulator is necessary.

There are a number of midi emulators available for linux, timidity, qsynth, fluidsynth to name a few.  You need to route your midi application through the emulator to produce sound.

---

### Post by tegnoto89 on 2009-01-23
Okay, I just installed qsynth, can somebody explain to me how to route the application through the emulator?

---

