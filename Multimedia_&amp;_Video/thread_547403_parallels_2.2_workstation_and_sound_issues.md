---
title: "parallels 2.2 workstation and sound issues"
date: 2007-09-10
forum: Multimedia &amp; Video
---

### Post by blargis on 2007-09-10
hello ladies and gents.  so here is the issue at hand.  I have been playing around with Parallels for the last few days and I have found a lot of good information on tweeking it for max performance. I had it running perfectly when out of the blue the sound stopped working.  note that it was working fine up until now. the green light on the speaker symbol does flash so i know that the sound is being sent... its just getting lost somewhere between my windows XP VM and my speakers...  also, all sound in my Ubuntu OS works perfectly.

things I have tried:
-made a new VM to see if it was a problem within the guest OS, however the fresh one had no sound as well. that lead me to believe it was Parallels that was causing the problem not the xp VM.
-reinstalled Parallels
-set all speaker settings to un-muted and max volume
-searched the forums desperately for an answer to my dilemma 

If anyone has some ideas for my next step please let me know because I am stumped.

-Ryan-

---

### Post by blargis on 2007-09-10
Well I fixed it! and I feel kind of silly. Turned out to be parallels sound output was configured incorrectly for some reason.  Either my sound card device number changed or I somehow got it set to the wrong setting... but anyhow I just had to click on the sound option and change the output device from /dev/dsp to /dev/dsp3 and it worked once more!  ](*,)

-Ryan-

---

