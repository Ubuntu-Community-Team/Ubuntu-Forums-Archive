---
title: "Sound works when I hear sound at startup (password screen)"
date: 2008-08-20
forum: Multimedia Software
---

### Post by smile me on 2008-08-20
Hi there,

being new at Ubuntu (Hardy), I wanted to explore the possibilities for audio and MIDI sequencers yet I got a bit frustrated sometimes.
This was because I could play several programs flawlessly,... but the day afterwards I was never sure they would still work.
My media player (Rythmbox) always gave me sound but I like to play around with sound and that was not always sure.
It appears that I can get sound out of them only when I heard the bongo sound that you hear when the password screen appears.
When I don't hear that sound I have to shut down the computer and restart it. This mostly works from the first or second attempt.
I would be very glad to understand what's behind this so I made this thread.
I am using ALSA and Jack and several programs such as LMMS, Fruity Loops under Wine (no succes with Reason)

Anybody had a simular experience?

---

### Post by markbuntu on 2008-08-20
Once you start jack, all your sound applications that do not use jack will not be able to play since jack takes over the sound card driver. You need to exit jack and close jack control to get them to work again. Some applications do not close jack when they exit and jack must be killed manually.

There are a few methods for getting your non-jack applications to play through jack. They are listed near the bottom of my guide here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

Have you tried using Hydrogen and Rosegarden with Ardour through jack. That combination seems to work very well for midi sequencing/recording since Hydrogen will supply the drums and Rosegarden the rest and Ardour can control them both for playback/recording.

---

### Post by smile me on 2008-08-23
**thanx a lot** for these manuals that was what I was looking for, not that it changed something so far. 
The problem is that I still have to learn how to configure Jack for Rosegarden and other software than LMMS.
Sometimes I have a feeling that Jack is configuring me instead of the other way around.
But I will give it a try or two offcourse,

thanx again

---

