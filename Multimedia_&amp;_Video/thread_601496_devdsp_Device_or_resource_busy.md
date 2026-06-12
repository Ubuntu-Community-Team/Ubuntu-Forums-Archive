---
title: "/dev/dsp Device or resource busy"
date: 2007-11-03
forum: Multimedia &amp; Video
---

### Post by grendelkhan on 2007-11-03
I just installed a fresh Gutsy on my new PC and after resetting my default sound card with asoundconf, now anything that tries to use /dev/dsp gives me the Device or resource busy.  I've even shut down everything using sound and I still get the error.  Even weirder is this:

```
sudo fuser -v /dev/snd/* /dev/dsp
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  grendel    6384 F.... mixer_applet2
```

I never had this problem on my old system, just since I installed the new one.  I have a SB Audigy SE, which is capable of mixing more than one stream and it's supported by alsa.

Any ideas?

---

