---
title: "Audacity playing back recorded stream at lower pitch than original"
date: 2013-01-31
forum: Multimedia Software
---

### Post by Bill Tetzeli on 2013-01-31
Okay, here's another one.  The last few weeks whenever I've tried to record streaming music, such as Pandora, on Audacity, it always plays back slower and at a lower pitch than the original stream.  It may be a sample rate problem.  When I take a standard 44.1 khz recording that I've made of a stream and reset the the sample format to 48 khz (no conversion, just how the recording's interpreted), it plays back at the correct pitch.  But then when I record a new stream at 48 khz, there it is again, playing back slow.  It seems no matter what I do, a stream recording is always going to play back slower than the original stream unless I reset the sample rate higher.

This wasn't a problem until a few weeks ago.  I actually did a complete reinstall of Ubuntu 12.10 today, hoping that would fix the problem, but as soon as I tried recording a new stream, the same thing happened.  Could this be the result of a recent system update?  The same problem occurs when I use Sound Recorder, btw.

I'm at a total loss on this.  Please help!  I don't want to go back to Windows!

Thanks in advance,

Bill

---

### Post by Bill Tetzeli on 2013-01-31
Weird - now the problem seems to have fixed itself.  Never mind.  Sorry to bother everyone.  Can't figure out for the life of me what caused it, though.

Hey, I just had a thought.  Back before computers we had these things called "recorders" and you could run a cord from what you were playing into it.  They were the Napster of their day.  I'm a taper and have two full sized and two handheld digital recorders.  Guess I can always run a patch out the headphone jack in a pinch. :-)

---

### Post by tgalati4 on 2013-01-31
Audacity has default clock rates set in preferences.  Perhaps your sound card has a different default clock rate.  Do some research on your sound card to determine what that default rate is:

```
aplay -l
```

---

