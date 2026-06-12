---
title: "too many mixers in ALSA"
date: 2008-09-22
forum: Multimedia Software
---

### Post by ishkabob on 2008-09-22
I'm sure there is an easy answer to this problem, but I didn't know how to search for it exactly.  There are too darn many mixers for my soundcard (Soundblaster Live 5.1) in my graphical alsa mixer.  When I pull up the alsa mixer, there are at least 8 sliders that obviously do the same thing that some of the others do.  I don't know if this is a failing of the mixer program, or alsa or what.  I'm trying to sort out some very complicated sound issues (multiple program microphone sharing with wine etc.) and I'm just having trouble keeping things straight.  This is compounded by having OSS and ALSA running at the same time.  I can pull up the volume slider in OSS, and then pull it up in ALSA and my sound will get really loud.  There should only really be a few volume sliders:

1.) master output volume
2.) gain for microphone jack
3.) gain for line input
4.) volume for internal analog CD-ROM audio

That should really be all I would think.  I'm hoping someone can help me get to that or at least set me straight.  Any help is greatly appreciated.

---

### Post by fooman on 2008-09-22
double click on the volume icon in the panel.  that brings up the alsa mixer...in the toolbar,  go to edit > preferences

just check/uncheck the options you would like to show in the mixer.

---

### Post by ishkabob on 2008-09-22
> **fooman said:**
> double click on the volume icon in the panel.  that brings up the alsa mixer...in the toolbar,  go to edit > preferences

just check/uncheck the options you would like to show in the mixer.

I understand that, but for example, I have an output slider for microphone, and an output slider for AC97.  Both of these sliders controls the output volume of my microphone through the speakers.  If I put the volume of AC97 all the way up, and then uncheck it so it disappears, what happens to it?  Does it stay on 100% volume output or does it go down to some nominal level?  And what does it [/I]mean[/I] to have two sliders control the same volume that don't seem to be tied to each other in any way.  Presumably there is only one hardware gain on the card itself, what is AC97 or microphone actually controlling?  I might just be angrily shouting into the wind right now, but I don't like not knowing how my software is interacting with my hardware.

---

