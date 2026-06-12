---
title: "How do you access the General MIDI patch bank in Ubuntu?"
date: 2006-09-01
forum: Multimedia &amp; Video
---

### Post by capsid on 2006-09-01
I had posted a thread a few days ago while I was trying to get up to speed with Qjackctl.  I had originally run into trouble because I could see my MIDI being processed in puredata, but couldn't hear anything, unlike in Windows, where it plays a grand piano sound.  I knew something was fishy when I tried to play a midi in a media player and also got nothing.  

So I did some research to find out what those cheesy default MIDI sounds are and I found this site:
[http://www.borg.com/~jglatt/tutr/gm.htm]("http://www.borg.com/~jglatt/tutr/gm.htm")

according to the site:> 
So to make MIDI Program Change messages of more practical use, Roland found it necessary to adopt a standard "patch bank". In other words, what was needed was to assign specific instrument sounds to specific patch numbers. For example, it was decided that patch number 1 upon all sound modules should be the sound of an Acoustic Grand Piano. In this way, no matter what MIDI sound module you use, when you select patch number 1, you always hear some sort of Acoustic Grand Piano sound. A standard was set for 128 patches which must appear in a specific order, and this standard is called General MIDI (GM). For example, patch number 25 upon a GM module must be a Nylon String Guitar. The chart, GM Patches, shows you the names of all GM Patches, and their respective Program Change numbers.

Nowadays, most modules (including the built-in sound modules of computer sound cards) ship with a GM bank (of 128 patches) so that it is easy to play MIDI files upon any MIDI module, without needing to edit all of the Program Change events in the file. 

So I know I can just drive an outside synth like alsamodular or whatever, but I'm doing some algorithmic composition stuff in puredata and it would be REALLY handy if I didn't have to synthesize a new sound every time I wanted to stimulate a program change.     

So does anyone know how to access your soundcard's default MIDI patchbank in Ubuntu???   

Thanks for your help.

p.s. If I can't figure this out, how will I listen to my Chrono Trigger MIDIs??? Oh the HORROR!!!

---

### Post by tatimmer on 2006-09-01
My sound card is nothing special, an old Soundblaster without a midi synth chip, on MSWindows I can play midi because Windows provides the midimapper.  When I switched to Linux over a year ago I have been using Timidity as my soft synth.  I generate my own midis from a text file using timidity and can also convert them to ogg. With timidity you must download a set of sound patch files that are freely available, though there is not a 100% gm set that is complete but I have most of the instruments that I need.

If you have Soundblaster Live or AWE64 or something with a midi hdwre synth on it I suppose you can use rosegarden or similar software.

The only drawback of timidity I know, it is slow in real time as it must convert midi data on the fly to produce PWM output for your soundcard.

tomstimiditytips may help.  Good luck.

---

### Post by capsid on 2006-09-03
hey, thanks for pointing me towards timidity.  I'm a bit noobish and got confused by your timidity tips page, but I was able to get stuff working with this guide:
[http://www.cs.cornell.edu/~djm/ubuntu/#timidity]("http://www.cs.cornell.edu/~djm/ubuntu/#timidity")

there's a section in there on setting up timidity to be your default midi player.  it doesn't use the freepats though, it uses some others.  i just got it working so I'll have to see how it holds up as the midi player for pure data.

I'm totally grateful to be able to use a distro as complete and actively maintained as ubuntu, but I'm wondering if having midi playback is something that should be made standard.   What do you suppose the reasons are for Ubuntu to not have a default midi playback device??? Licensing? CPU hog? Is it just obsolete now that webpages use sample playback?

Anyway, thanks for the help.

---

### Post by capsid on 2006-09-03
Ok, so I tried to send MIDI from puredata to Timidity but there isnt a midi-in in Jack Control for timidity.  I tried starting timidity with the option '-iA' to start run it in alsa sequencer mode (which i assume would make it show up in Jack Control), but I get this error:
> ALSA lib pcm_dmix.c:819: (snd_pcm_dmix_open) unable to open slave


any ideas?

---

### Post by christhemonkey on 2006-09-03
> **capsid said:**
> Ok, so I tried to send MIDI from puredata to Timidity but there isnt a midi-in in Jack Control for timidity.  I tried starting timidity with the option '-iA' to start run it in alsa sequencer mode (which i assume would make it show up in Jack Control), but I get this error:


any ideas?

You can run it with options -Oj to give jack output, and with -irA to give a ALSA midi server input.
(i think)

---

