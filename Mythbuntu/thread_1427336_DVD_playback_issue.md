---
title: "DVD playback issue"
date: 2010-03-11
forum: Mythbuntu
---

### Post by sfuse on 2010-03-11
I've been playing with DVD ripping and I noticed that when I start playing a movie, either from a rip or from the DVD player, that the video is running too fast.  Looks like around 2x and the audio gets way out of sync.  If I ffwd then play everything works correctly.  I have seen where others have had this problem but I haven't seen a fix other than switching to a different player than mplayer.
 
Is there some setting to tweak to fix this problem?  Anyone have suggestions on the best way to fix this issue?
 
I am running a new install of mythbuntu with mythtv 0.22

---

### Post by larsolav on 2010-03-11
Have you updated the system since you installed? I had a similar problem with funky audio on some of my ripped ISOs, but that got fixed a few weeks ago through an update.

---

### Post by sfuse on 2010-03-11
Yeah, I did that first thing after OS install and before I started installing hardware drivers.  I installed the OS only about a week ago so should be good.  

I did one other update since then and wound up with a new kernel and had to re-install the driver for my tuner card.  It's OK though, now I have a script to do that automagically next time. :)

 Anyway I don't think my problem has been addressed with an update.

---

### Post by larsolav on 2010-03-11
Hmm, how about maybe trying to Activate Auto Builds here: [http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds)
and then open up Update Manager and check for updates?
It may be that the mythtv fixes you need can be obtained this way...

---

### Post by sfuse on 2010-03-11
Thanks larsolav, that seems to have fixed the problem!

I still have an issue with 1 of 4 ripped videos on my machine but that video has other odd issues possibly related to something with the source DVD.

Thanks again.

---

### Post by larsolav on 2010-03-12
Glad you got it sorted out! The one funky DVD rip wouldn't happen to be from a Sony or Disney DVD? They add stuff to them to trick systems like mythtv into crashing the play back. I have some older Disney DVD rips that played fine in myth 0.20, and would not play in myth 0.21. The internal player in myth 0.22 now plays those older DVD rips,but newer Disney DVDs are a bit trickier to get working...

---

### Post by sfuse on 2010-03-12
No it's a Warner Bros.  It has both wide screen and 4:3 versions on the same DVD.  The wide screen won't play off DVD or ISO rip,  I get an error something about a major video error.  The 4:3 does play on both but with same issue as before.  
 
What's odd though is I can rip the just wide screen version by itself using perfect quality and it plays fine except the default audio is in Spanish.  I have to manually change audio tracks after I start playing.
 
I think I need to go throw this thing in just a normal DVD player again and see if it works cuz I seem to remember having problems there as well.

---

