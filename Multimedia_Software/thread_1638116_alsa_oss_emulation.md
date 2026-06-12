---
title: "alsa oss emulation"
date: 2010-12-05
forum: Multimedia Software
---

### Post by mich@ on 2010-12-05
I want to use an elderly software , but it needs oss. Sadly the alsa oss emulation modules have gone missing since maverick.. and it doesn't work with aoss.

Could anyone tell me what would be the best way to reactivate oss emulation in alsa, or if there is a good reason that I should not ? 

I don't really now how to rebuild a kernel, and I don't think it is necessary. I guess, It would be enough to delete alsa, and reinstall it from the source rather from than the ubuntu repository. But is that necessary ? If so I am willing to "read" and find out how that is done...

---

### Post by whitepine on 2010-12-09
Pulseaudio can emulate oss by using papsd, which probably is already installed.
Just run:

papsd /path/to/your/game

You can add this to your game in the applications menu by right clicking applications on your panel, choosing edit menus, find your game, choose properties, and adding papsd before the path to your game in "command".

This worked for me when trying to run Jardinains.

This should have been padsp /path/to/your/game not papsd.  Sorry for the mistake.

---

### Post by Vilentviolet on 2010-12-12
I've also got the same problem going. I'm trying to run an elderly program that doesn't work with aoss, but the thing is... I completely gutted out PulseAudio from my system! I'm trying to avoid reinstalling it at all costs if I can, so given this dilemma, how do I get good OSS emulation going in ALSA alone?  When I attempted aoss <program> in the terminal, this is what I get when the program loads to this point: ```
Initializing Sound
  Couldn't set audio frequency

```
And then a popup window comes up saying it couldn't initialize the sound.

---

