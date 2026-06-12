---
title: "Looking for Autotune/pitch control"
date: 2007-11-11
forum: Multimedia Production
---

### Post by nicholaspaul on 2007-11-11
I'm looking for a program that is similar to [Melodyne]("http://www.celemony.com/cms/") that will allow me to shift individual notes in a wav file. It works with audio files in a similar way to editing MIDI files. 
Has anyone heard of anything that does that for Linux?

---

### Post by nalmeth on 2007-11-11
[http://mturkmedia.typepad.com/transcribers/2006/08/pitch_shifting_.html](http://mturkmedia.typepad.com/transcribers/2006/08/pitch_shifting_.html)
found googling linux pitch shift

Looks like the best solution is a LADSPA plugin, and you can use any LADPSA capable application to host it.
Audacity and jokosher are simple editors that you can use the plugin with. 

To install the plugins you need:
```
sudo apt-get install tap-plugins
```

---

### Post by nicholaspaul on 2007-11-12
I googled autotune linux. 

Pitch shift is easy. I'm looking for something that will let you control the pitch of individual notes by increments of semitones, not shift the pitch of the entire file.

---

### Post by Banter on 2008-02-07
I'm not an audio guru, but I believe if you want to change the pitch of an individual "note" you need to have that note isolated on an individual channel (microphone channel or whatever) and work with that stream of data specifically.

---

### Post by eric71 on 2008-02-08
Probably the best way to do this is with Audacity using the "Change Pitch without Changing Tempo"  effect. Audacity can apply these effects on just the portion of the file you select, not the whole file such as with Ardour for instance. Zoom the horizontal axis so you can really select just what you want and apply the effect. This is the only way I can think of in linux to fix individual notes in a .wav file.

[IMG]http://www.hotlinkfiles.com/files/964233_9cmcw/zoomed.jpg[/IMG][IMG]http://www.hotlinkfiles.com/files/964234_wouyp/pitch.jpg[/IMG]

Alternatively, if you are looking for automated pitch correction for the whole track, then I would use fst or dssi-vst to host a vst pitch corrector. i've had good luck with Gsnap in Rosegarden for my terrible vocals. [http://www.gvst.co.uk/gsnap.htm](http://www.gvst.co.uk/gsnap.htm). But to fix just specific individual notes, the Audacity way is best.

---

### Post by Killes on 2008-07-13
Hohoho, melodyne is so very very much more than pitch shifting, i'm afraid theres no equivalent on Linux, apparently version 3 works on linux with dssi vst [http://ladspavst.linuxaudio.org/?q=node/2288]("http://ladspavst.linuxaudio.org/?q=node/2288")
But im having trouble, the version 3.1 I have seems to have a dozen vst dll's that work together instead of 1 dll so I dont know which to launch how...

---

