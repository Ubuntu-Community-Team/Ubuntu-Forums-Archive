---
title: "simultaneous spdif AND analog output"
date: 2008-05-01
forum: Multimedia Software
---

### Post by TheKorn2 on 2008-05-01
OK, I think this should be a simple .asoundrc file, but I can't make heads or tails of the alsa wiki on the subject ( [http://alsa.opensrc.org/home/w/org/opensrc/alsa/index.php?title=.asoundrc](http://alsa.opensrc.org/home/w/org/opensrc/alsa/index.php?title=.asoundrc) ).


What I want to do is have the system output to both the SPDIF jack and the analog outputs at the same time.

Here's what I have for a .asoundrc so far:

```

pcm.!default {
        type hw
        card 0
        device 1
        }

ctl.!default {
        type hw
        card 0
        device 1
        }

pcm.digout {
        type hw
        card 0
        device 1
        }

pcm.anaout {
        type hw
        card 0
        device 0
        }

```

That gets me on the right path.  If I do an "aplay song.wav" , it will come out the SPDIF output.  (That's the default, so it's expected.)  

If I do an "aplay song.wav -D digout" , also through SPDIF (expected).  

If I do an "aplay song.wav -D anaout" , I get sound through the analog outputs (expected).


So I know where everything *is*.  But I can't figure out how to get alsa to use more than one output at a time.  What I'd like to happen is for alsa to copy the stereo output to the analog section.

Ideally, it's also read AC3 going out spdif and send the first two channels via the analog out as well.

Any help?  I know I need to define a slave, but for the life of me can't even being to make heads or tails of that ALSA wiki entry above.

Thanks in advance!

---

