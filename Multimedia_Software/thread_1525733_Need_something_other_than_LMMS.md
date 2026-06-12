---
title: "Need something other than LMMS"
date: 2010-07-07
forum: Multimedia Software
---

### Post by uqbar on 2010-07-07
Hi all.
It's now 3 months I'm using LMMS for music composition down to the .WAV file creation from samples and soundfonts.
It's as simple in the concept as buggy in the implementation.
I'm using a PPA (tobydox) from Launchpad but still get some weird things like the application dying suddenly (and before any project save has been done).
Is there any advise for a better or at least more mature software
for similar tasks?

---

### Post by cchhrriiss121212 on 2010-07-07
Yes, there are other options that should manage what you want to do, but they all rely on the jackd sound server which has a small learning curve to it. Jack and the apps that use it work in a modular fashion, as opposed to all-in-one type programs like LMMS.
Try downloading the ubuntustudio-audio package from synaptic, which has many great things in it to get you started. 
For multi-track recording: Ardour
For multi-track recording plus MIDI: Qtractor
Drum sequencer: Hydrogen
Synths: phasex, zynaddsubfx, bristol

Look at this guide for jack setup help:
[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)
Particularly the realtime setup section.

There's also this ppa which will give you more music software:
[http://ubuntuforums.org/showthread.php?t=1350304](http://ubuntuforums.org/showthread.php?t=1350304)

---

### Post by uqbar on 2010-07-07
Is there any tutorial about this "scattered" approach?
I need to understand, for example, how difficult is in a piece to replace some instruments with others taken from another soundfont...

---

### Post by dino99 on 2010-07-07
linux apps base

[http://linuxappfinder.com/multimedia](http://linuxappfinder.com/multimedia)

---

### Post by uqbar on 2010-07-07
> **dino99 said:**
> linux apps base

[http://linuxappfinder.com/multimedia](http://linuxappfinder.com/multimedia)

Overwhelming ...

It seems that ardour and rosegarden would be the right product to me.
Do you actually know whether these two packages can "replace" LMMS?

---

### Post by cchhrriiss121212 on 2010-07-07
> **uqbar said:**
> Overwhelming ...

It seems that ardour and rosegarden would be the right product to me.
Do you actually know whether these two packages can "replace" LMMS?
Yes they can, but like I mentioned they will just work in a different way. I would recommend using qtractor instead of ardour+rosegarden to save a bit of efficiency.

> Is there any tutorial about this "scattered" approach?
I need to understand, for example, how difficult is in a piece to replace some instruments with others taken from another soundfont...
I saw a youtube tutorial somewhere on the studio forums, but I can't remember where, it was in someone's sig. I think the best way to learn using linux/jack audio is to just try it out, and ask for help if/when you get stuck. I'm not quite sure what you mean by replace, but the best soundfont program I have used is qsynth so you should look into that. 

Here is a screenshot of patchage which is what you can use to view all your connections:
[IMG]http://img14.imageshack.us/img14/7861/screenshot1law.png[/IMG]

The blue ports show audio inputs/outputs, and the green show midi inputs/outputs. You can connect things manualy, but when loading a project the connections will be maintained from the last save point along with the audio data.
It is certainly more complicated than LMMS, but gives you so much more freedom to route your audio wherever you please and make some great sounds.

---

### Post by uqbar on 2010-07-07
> **cchhrriiss121212 said:**
> Yes they can, but like I mentioned they will just work in a different way. I would recommend using qtractor instead of ardour+rosegarden to save a bit of efficiency.

This sounds a good hint ... despite it seems to me much more sound oriented than music composition oriented ...

> **cchhrriiss121212 said:**
> 
I saw a youtube tutorial somewhere on the studio forums...

I'm too old for youtube tutorials. I need to read, think, test ... Text is good, while videos are evil to me and to my weak sight.

> **cchhrriiss121212 said:**
> 
Here is a screenshot of patchage which is what you can use to view all your connections:
...
The blue ports show audio inputs/outputs, and the green show midi inputs/outputs. You can connect things manualy, but when loading a project the connections will be maintained from the last save point along with the audio data.
It is certainly more complicated than LMMS, but gives you so much more freedom to route your audio wherever you please and make some great sounds.
Nice, thanks. This shows a lower level phylosophy than LMMS which tries to balance power and simplicity. I need to study these softwares.

If there's some extra hint out there, I'll be happy.

---

