---
title: "Wierd Sound Issue"
date: 2009-01-21
forum: Multimedia Software
---

### Post by newbie63 on 2009-01-21
Running 8.10 on Dell 8600 laptop.
Loaded drivers for MP3 - Works fine
Loaded drivers for CD player - works fine
Loaded drivers for DVD - works fine
Loaded drivers for Flash (YouTube video) - works fine
Created custom sound theme with .wav files - doesn't work

The default sound plays on bootup and I get a beep when email arrives.  These are two of the items that I have assigned .wav files to.  Not a showstopper by any means just annoying.

Thanks, Newbie63

---

### Post by hal8000 on 2009-01-21
The wave file you created may not be compatible. What sampling did you use and what app did you use to convert it?

Sounds are stored in /usr/share/sounds

The command "file" will give you sample rates and formats, so this is possibly where the problem lies

anc@orac:/usr/share/sounds$ file startup.wav 
startup.wav: RIFF (little-endian) data, WAVE audio, Microsoft PCM, 16 bit, stereo 44100 Hz

As can be seen, the startup wave is a microsodt PCM 16bit sampled at 44.1kHz
Hope that helps

---

