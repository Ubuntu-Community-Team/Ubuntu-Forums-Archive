---
title: "No MIDI sound in Rosegarden....."
date: 2007-05-03
forum: Multimedia &amp; Video
---

### Post by Izobalax on 2007-05-03
Are there any composers here in the Ubuntu community?

Although I've mainly been with Ubuntu, I have tried other distros as well. They all, however, share one feature: the ***total*** inability to play MIDI in Rosegarden. 

The ***really*** strange thing is that I can get MIDI drum sounds in Hydrogen. :confused: Yet, no MIDI in Rosegarden. 

Basically, I installed on my system all the packages from the Ubuntu Studio wiki page, so I have all those applications and stuff on my system. But I'm out of touch with the whole technical aspect of MIDI sequencers and such. I need help.

What am I doing wrong?

/izo (*who'd love to start MIDI sequencing again*)

---

### Post by monstermunch on 2007-05-03
You need to have a MIDI player running (I'm not sure what the name of these things are...) and tell Rosegarden to send what it wants to play to this. I plug my MIDI cable from my piano into the machine, tell Rosegarden to output to this and MIDI plays through my piano. qsyth is a sequencer you can use; install it, start it up and then tell rosegarden to use it as output.

---

### Post by Auria on 2007-05-03
Midi on linux can be a tough one...

i have never used Rosegarden itself, but i know how to get midi working in ALSA. (from their website, Rosegarden seems to use ALSA)
i'm not sure what specific steps you did.
you'll need to install a softsynth if your sound card doesnt support midi or is not supported (this is most likely the case as very few cards do) easierst way is to install timidity++ from the repositories (might be called just timidity). Then you'll need to run it as ALSA deamon before you can start using ALSA and midi

timidity -iA -B2,8 -Os

if you get errors when you run that you may not to do "sudo modprobe something" unfortunately i dont remember which one and im not in ubutnu right now so cant remember.EDIT: from what i read on  a website i think it's sudo modeprobe snd-seq

then you can configure rosegarden to use the midi port this command outputs (leave the terminal open until you dont need midi anymore) From a website, it should be in Composition > Studio > Midi Hardware (names may differ, the website i found was in french and im translating back to english)

---

### Post by Izobalax on 2007-05-04
> **Auria said:**
> Midi on linux can be a tough one...

i have never used Rosegarden itself, but i know how to get midi working in ALSA. (from their website, Rosegarden seems to use ALSA)
i'm not sure what specific steps you did.
you'll need to install a softsynth if your sound card doesnt support midi or is not supported (this is most likely the case as very few cards do) easierst way is to install timidity++ from the repositories (might be called just timidity). Then you'll need to run it as ALSA deamon before you can start using ALSA and midi

timidity -iA -B2,8 -Os

if you get errors when you run that you may not to do "sudo modprobe something" unfortunately i dont remember which one and im not in ubutnu right now so cant remember.EDIT: from what i read on  a website i think it's sudo modeprobe snd-seq

then you can configure rosegarden to use the midi port this command outputs (leave the terminal open until you dont need midi anymore) From a website, it should be in Composition > Studio > Midi Hardware (names may differ, the website i found was in french and im translating back to english)
It worked! You're a star! Thank you! :grin:

/izo

---

### Post by aonegodman on 2007-12-26
> **Izobalax said:**
> It worked! You're a star! Thank you! :grin:

/izo

Glad to hear someone got it to work!

I put the code in my Terminal and it just sits there never going back to input string $

Still searching the forum for answers . . . . .

---

