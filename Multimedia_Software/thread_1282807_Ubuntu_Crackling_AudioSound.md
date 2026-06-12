---
title: "Ubuntu Crackling Audio/Sound"
date: 2009-10-04
forum: Multimedia Software
---

### Post by fermulator on 2009-10-04
So this evening I booted my system.  Strangely, all of a sudden, any sound that *tried* to come out of the speakers was a sort of crackling sound.  I quickly eliminated my speakers as the problem (they worked fine connected to another device).

Did some quick Googling, and stumbled upon this thread: [http://ubuntuforums.org/showthread.php?t=904677](http://ubuntuforums.org/showthread.php?t=904677).  There were lots of solutions and reports of people fixing the problem, but what worked for me (and I believe to be the CORRECT solution) is that the PCM slider was at 0% in the alsa mixer.

_**Steps to Fix Crackling Audio**_:
 1. Right click on Volume Control
 2. Choose Preferences
 3. Under the "Playback" tab, ensure the PCM slider is NOT 0% (I like to keep it around 85%...)

I have confirmed this to be the crackling problem I experienced, because if the slider is at 0%, the crackling comes back, but as soon as it's not 0% (even 1%, or 100%), the crackling stops.

*What's the deal with this*?
 1. Why/How does the PCM slider go to zero? (I know it's not just me ...)
 2. Why do we here crackling at 0% only? ...

All too strange...

---

