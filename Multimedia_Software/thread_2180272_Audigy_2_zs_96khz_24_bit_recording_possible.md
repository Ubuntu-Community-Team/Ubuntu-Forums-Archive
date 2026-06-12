---
title: "Audigy 2 zs 96khz 24 bit recording possible?"
date: 2013-10-12
forum: Multimedia Software
---

### Post by gravysteak on 2013-10-12
Hi.
Currently using JACK I can seem to get 96khz playback on the p16v hardware device but the input only finds 2 channels and I can't seem to get any input out of them. I've tried changing hd channel capture and hd source in alsamixer.
Does anyone know wether the inputs currently work at all through p16v? If they do can you record channels simultaneously like is possible with emu10k2 dsp?

---

### Post by gravysteak on 2014-02-21
I had another go and got it working. 
If the hd source and channel in alsamixer isnt set to the right setting jack will stop working and wont start up again properly. 
I tried killing jack and re runing it and it wouldn't work and I couldn't find out why. Does anyone has any hints to get it to run again??

Anyway the main thing is set your hd channel (2 for the drive bay rca. I guess 1 is rear line in.) and source (i2s) to the correct setting and reboot the computer then jack will start working at 96khz. As far as I could tell you can only record in stereo but it outputs in 8 channel.

---

