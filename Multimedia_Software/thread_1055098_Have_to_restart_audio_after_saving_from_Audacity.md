---
title: "Have to restart audio after saving from Audacity"
date: 2009-01-30
forum: Multimedia Software
---

### Post by sydbat on 2009-01-30
Audacity 1.3.4 on Hardy.

I am currently recording my vinyl. I can record an album side (or single song) just fine using my USB turntable (the quality is quite good). However, when I save the file then try to record the next album side, Audacity no longer wants to play nice. I get this error message```
Error while opening sound device. Please check the input device settings and the project sample rate.
```I have to go into a terminal and kill the sound drivers and reinitialize them before I can continue recording.

It is annoying, but I can work with it if there is no other solution.

Is this an Audacity bug? Would downloading the newest version circumvent this problem?

Thoughts?

---

### Post by ajgreeny on 2009-01-30
This usually happens if you have another audio application open, eg, if you open mplayer or totem or another audio player, to listen to your newly recorded audio and then try to go back to audacity to record again.  It is much easier to listen to your recording using audacity, and then you should be able to swap back and forward between record and listen without a problem.  That's the way I do it.

The same sort of thing happens sometimes when trying to record direct from the sound card if I'm listeneing to and recording an internet radio broadcast.  I have to start audacity first then go to the url for the audio stream; the other way round gives the same error message you get, I assume because mplayer plugin is running.

I don't think it's a bug. it is simply the way audacity works with the sound server in linux.

---

### Post by sydbat on 2009-01-30
I thought that too. But even when I do not listen to the track after exporting it, I still get the above error message. Only after exporting. Weird.

---

### Post by ajgreeny on 2009-01-30
If it helps this is my sound system setup which may be different to yours, and as you can see I use pulse but in audacity I use alsa.  Try that, if yours are different and see if it helps.

---

### Post by sydbat on 2009-01-31
Thanks for all your help.

I updated to 1.3.5 and it *seems* to have cleared up the problem. If anything changes, you know there will be another post...

EDIT - I cannot find the Solved option in Thread Tools. If a Mod stumbles upon this thread and has **THE POWER**, please mark as Solved for me. Thank you.

---

