---
title: "[SOLVED] Brief Sound, Then-Nothing"
date: 2008-08-09
forum: Mythbuntu
---

### Post by Ronno6 on 2008-08-09
I have Mythbuntu 8.04 up and operating-almost. When I open "Watch TV" I get about 1 second of sound, before the picture is displayed, then, nothing! 
Machine is Dell Optiplex Pentium 4 2.8ghz, 2gig RAM, Fusion HDTV5 RG Gold tuner, PNY nVidia GeForce 6200 AGP video card, sound is onboard. Sound is enabled in BIOS.In Mythbuntu frontend setup I am using the ALSA Default settings driver. In Ubuntu settings I have tried all available possibilities.

The sound worked fine when this was a Windows machine.

Where do I go from here?

---

### Post by Ronno6 on 2008-08-09
Through massaging the settings in the capture card setup in the Backend, I now have sound, but it is somewhat garbled. Video is also a bit jerky. It seems that the 1 second of good sound I get is in sync with the current broadcast, which is playing in an adjacent room on a TV. When the picture and garbled sound kick in, there is a delay from the current broadcast of a fraction of a second. 
Does this provide any clues?
BTW- the tuner has an analogue output cable that is connected to the CD audio input on the MB.

---

### Post by Ronno6 on 2008-08-09
I disconnected the internal analog cable. That was the source of the clear audio burst I was getting when I began to watch TV. 
Now, the audio is,as before, somewhat garbled. There is kind of a whining tonal quality to the sound, like a carrier or something. But, as it wasn't present through the analog cable before Muthbuntu began processing the playback, I can't think the problem to be with the tuner card or onboard audio. 
Maybe it is a PCI thing?

---

