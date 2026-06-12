---
title: "MIDI problems in Rosegarden4"
date: 2006-06-24
forum: Multimedia &amp; Video
---

### Post by mjshepherd on 2006-06-24
Hi There,

I've been trying to get MIDI sound to play in Rosegarden4 for some time - it tells me that "MIDI OK, Audio OK" but nothing comes out of the speakers when i play my sequences. I found a HOWTO (which i now realise were for Warty) and tried to follow them, but have come across some problems, which i wondered anyone'd help me with?

I think i have most of the packages listed in the HOWTO, but couldn't get alsa-headers, or alsa-modules-2.4.26-1-386 through apt-get. Is this a problem? Are they defunct? How do i solve it?

I have a midi-enabled soundcard (which works on my windows partition) and have installed awesfx. I have also intalled Fluidsynth (with qsynth front end) just in case - I guess i shouldn't need this - should i get rid of it?

An lsmod lists all the necessary lines mentioned in the HOWTO, and more besides, so didn't do any "sudo modprobe"ing, did i need to?

I downloaded the "Gort's_Synth.sf2" zipfile and have extracted it into my home directory. However, when i run the command

sfxload Gort's_Synth.sf2

I don't get a $ command line, but a > line instead. I don't know what to do at this point. Exactly the same thing happens if I try to load this soundfont to Fluidsynth using your instructions. Please help! I just end up shutting down the terminal and hoping for the best, but with no results.

Cheers,

Matthew

---

### Post by yurtboy on 2006-07-14
Did you get this working?
Kmid has the same problem.
Though if I do timidity /directory/file.mid
it will play the file?
Let me know how it goes
Thanks
Al

---

