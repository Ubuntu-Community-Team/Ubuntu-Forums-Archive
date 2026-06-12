---
title: "inconsistant sound"
date: 2009-02-13
forum: Multimedia Software
---

### Post by tranceponderer on 2009-02-13
Sometimes when I start my computer I wont be able to get any sound off out of my computer. Then after restarting (without changing any settings) I will get sound. It's not a given that restarting will give me sound though. Its like I roll the dice everytime i boot up. To make it even more confusing (for me at least), sound from flash will always work. i.e. youtube always has sound but a downloaded video (on every player) will or wont. I suppose depending on how it feels.

I have everything set to use pulseaudio
in the sys-prefrenses-sound window the test feature will only work for oss, not alsa, or pulse. Even when the sound is working just fine.
I was originaly just using oss but then flash wont play sound. 
im using a sb audigy
Where should I look?
Would reinstalling pulse and alsa help?
thanks
~karl

---

### Post by tranceponderer on 2009-02-23
::Update::

when audio is not working on the computer and i do the test for oss sound in preferences/sound i get this error message

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback. Device is being used by another application.

When it is working and i test it, i will get the beep sound.
when i do the test for pulse it will never beep.

when i originally set up my sound it was following this guide
[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

### Post by Kevitivity on 2009-03-17
I have the same problem.  Audio works for a day or so, and then stops working.

---

