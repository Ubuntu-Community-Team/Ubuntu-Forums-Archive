---
title: "Pulse Audio On = Grainy Sound , Pulse Audio Off = Fine and Dandy"
date: 2008-11-23
forum: Multimedia Software
---

### Post by unc0nn3ct3d on 2008-11-23
So this one kind of crept up on me, I guess I just got used to the poor sound quality but today I was noticing a slightly grainy texture to the sound as I played my music in Exaile.. I didn't really think it was major until I started fiddling, shut down PulseAudio and used ALSA as the default Sink.. Holy Crapola, the difference was huge, Pulse is just turning crystal clear music into this grainy crap and I don't know why.. I've gone into the pulseaudio applet, checked all my levels and everything seems fine.  But the moment I turn it on the quality goes to hell, the moment it is off the quality becomes crystal clear.. 

Anyone have / solve this problem?

---

### Post by kostkon on 2008-11-25
> **unc0nn3ct3d said:**
> So this one kind of crept up on me, I guess I just got used to the poor sound quality but today I was noticing a slightly grainy texture to the sound as I played my music in Exaile.. I didn't really think it was major until I started fiddling, shut down PulseAudio and used ALSA as the default Sink.. Holy Crapola, the difference was huge, Pulse is just turning crystal clear music into this grainy crap and I don't know why.. I've gone into the pulseaudio applet, checked all my levels and everything seems fine.  But the moment I turn it on the quality goes to hell, the moment it is off the quality becomes crystal clear.. 

Anyone have / solve this problem?
Try to change the *fragments* and *fragment-size* values in your .pulse/daemon.conf file to these
```
default-fragments = 8
default-fragment-size-msec = 5
```
If you don't have a *.pulse/daemon.conf* file then you can change the global one at */etc/pulse/daemon.conf* or just create the *.pulse/daemon.conf* file yourself.

You could some more configurations, just check the *Appendix B* in [this thread]("http://ubuntuforums.org/showthread.php?t=789578").

---

### Post by unc0nn3ct3d on 2009-05-08
Wow, I think I may have JUST found the bloody solution to this problem that has plagued me for oh so long

Posted about my near religious elation and experience here: [http://blog.netflowdevelopments.com/2009/05/07/sound-quality-with-pulseaudio-finally-restored-no-more-slightly-grainy-music/](http://blog.netflowdevelopments.com/2009/05/07/sound-quality-with-pulseaudio-finally-restored-no-more-slightly-grainy-music/)


> I had found a few days back while going through the hellish experience that is Amarok 2 that if I was running pulse as root the audio quality would resume.  But I never really put two and two together as my settings in /etc/pulse/daemon.conf were identical to those in ~/.pulse/daemon.conf .  In fact I even deleted the latter and replaced it with the former.  What as most perplexing is that I would adjust the resampler method from something like speex-float-1 all the way to src-best-quality without any change in CPU usage or any change in quality.

But today I went one step further as I noticed that in my ~/.pulse/ directory I was missing 3 files:  "client.conf , default.pa, and system.pa" .  I am not sure why these were missing, pulse loaded fine without them but they were.  This was the only difference now between my /etc/pulse and ~/.pulse so I went and deleted everything from ~/.pulse and replaced it with what was in /etc/pulse  and VIOLA!!  I now have perfectly crystal clear sound and what a bloody relief.

---

### Post by psyke83 on 2009-05-08
> **kostkon said:**
> Try to change the *fragments* and *fragment-size* values in your .pulse/daemon.conf file to these
```
default-fragments = 8
default-fragment-size-msec = 5
```
If you don't have a *.pulse/daemon.conf* file then you can change the global one at */etc/pulse/daemon.conf* or just create the *.pulse/daemon.conf* file yourself.

You could some more configurations, just check the *Appendix B* in [this thread]("http://ubuntuforums.org/showthread.php?t=789578").

The fragment settings will affect buffering (so it only has the potential to alleviate stuttering). The original poster may well be noticing the horrible resampler (src-linear) used in Jaunty's PulseAudio.

See Appendix B of my PulseAudio guide, and I recommend trying speex-float-1 (which was used in Intrepid). Consult the listing of resamplers in the guide if you want to try a higher-quality resampler.

---

