---
title: "Gtick blocked by Jack despite alsa-oss"
date: 2008-02-24
forum: Multimedia &amp; Video
---

### Post by raydar on 2008-02-24
I'm trying to use Gtick (metronome) at the same time as I use Creox (realtime audio effects).  Creox needs Jack, and Jack has to be started before anything else.  But if I launch Gtick after Jack is running, I get the error 
[INDENT]"Couldn't start metronome. Please check if specified sound device and sample file are accessible." [/INDENT]
when I click "Start" in Gtick to make it begin ticking.  (If I launch Gtick before I start Jack, Gtick works fine, outputting the appropriate sound.) 

 I eventually discovered that Gtick uses OSS and Jack uses ALSA, and I figured that was the root of the problem; I subsequently found the alsa-oss package and installed it because it purportedly lets OSS applications output sound through ALSA (unless I misinterpreted something).  But even after a reboot, nothing has changed; I still get the above error message from Gtick if I try to start it ticking after Jack is running, notwithstanding alsa-oss.  

Looking at the Gtick FAQs, [http://www.antcom.de/gtick/](http://www.antcom.de/gtick/) , I saw that I should check my /dev folder to "Make sure /dev/dsp* (e.g. /dev/dsp0) exists and GTick is configured to use it."  What I have in /dev are "dsp" and "dsp1," and Gtick was configured (in its Edit-->Preferences) to use /dev/dsp.  So just to see what would happen, I reconfigured Gtick to use /dev/dsp1.  That had the effect of Gtick *not* throwing up the above error message when I click "Start" to make it begin ticking, but it also caused there to be no ticking sound whether Jack is running or not.  Also, regardless of whether I have Gtick using /dev/dsp or /dev/dsp1, neither Gtick nor any OSS-type entry shows up in the Connections window in Jack.

Do I need to configure the alsa-oss package somehow, or configure Jack to incorporate or recognize it?

---

### Post by hyperair on 2008-02-24
The alsa-oss package comes with a binary wrapper "aoss". The way to use it is to run it like this:
```

aoss <appname>

```

In your case it should be something like ```
aoss gtick
```

I could be wrong though.

---

### Post by raydar on 2008-02-24
Thanks, hyperair--I wasn't aware of that, and that's sure good to know.  Didn't fix this issue unfortunately; I typed
[INDENT]aoss gtick[/INDENT]
and got
[INDENT]/dev/dsp: Device or resource busy[/INDENT]
and also tried having Gtick use /dev/dsp1 after launching Gtick via aoss, and there was no difference from using /dev/dsp1 before (no error, but no output). :(

Well hey, if the problem is Jack hogging /dev/dsp, and if /dev/dsp1 is not being hogged but it's output isn't "getting through," is there a way I can route /dev/dsp1's output to Jack's input?  (I'm thinking /dev/dsp1 might be the on-board sound that I'm not using, while /dev/dsp is the PCI sound card which I am using.)

---

