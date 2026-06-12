---
title: "Can record, but won't play"
date: 2009-02-10
forum: Multimedia Software
---

### Post by quazi on 2009-02-10
Hey, I've got a line-in cable running to my laptop from which I can record sound, but it won't route it to my speakers.  For example, I'd like to be able to play an mp3 player/nintendo wii through the speakers connected to my PC.

I'm running Intrepid on a Dell Precision 65M with a Sigmatel STAC9200 chipset.  I've gone through alsamixer far too many times and fiddled around with every setting that could come to mind, but I hear nothing through the speakers.  I've tried using audacity to simultaneously record and play, but that causes the program to crash.

Any tips?

---

### Post by quazi on 2009-02-17
I'd like to add that it works (not really fine, but it works) in OSSv4, but I'd like to stick with the officially supported soundsystem this time around.  Any chance upgrading to Jaunty would help me?  I'm already using Alsa v1.0.19

---

### Post by quazi on 2009-04-11
So, I've managed to find a workaround in 9.04.

Under System->Preferences->Sound, if Sound Capture is set to Pulseaudio, hit Test and it will output the sound from the line-in to the speakers.

---

