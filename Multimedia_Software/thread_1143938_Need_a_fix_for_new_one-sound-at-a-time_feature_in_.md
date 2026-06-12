---
title: "Need a fix for new one-sound-at-a-time feature in ubuntu"
date: 2009-04-30
forum: Multimedia Software
---

### Post by Jive Turkey on 2009-04-30
I really don't understand the sound system and related bundle of packages that make it work (or make it not work).  I know it worked great for me on 6.10 through 8.10 right out of the box, I think that previously it was pure ALSA.  I guess there was something seriously wrong with that so the developers threw in OSS and pulseaudio as well and now my sound device will only work for one application at a time (seemingly on a first come first serve basis).  Anoyingly I have to kill any audio app before another app make sound.  If I don't, either app might freeze, or maybe the second one will run without any sound.  ei: rythmbox + firefox@youtube, no sound in firefox as it locks up.  Before I could pause rythmbox and watch a video just fine. Currently I have to kill rythmbox before starting firefox if I want sound.

I'm using Ubuntu 9.04 x64 and my on board sound chip is identified as "HDA Intel ALC888"  though its actually a realtek branded chip on the mobo.

---

### Post by Jive Turkey on 2009-04-30
I found this thread [http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)
but after setting playback to PulseAudio all I can get is crackling noise.

Has anyone had any success uninstalling pulseaudio and getting alsa to work like it used to in prior versions of ubuntu.  

Jaunty is wonderful in every other aspect, I wish they hadn't hosed the audio so badly.

---

### Post by psyke83 on 2009-04-30
Please see my guide on PulseAudio.

After following the steps, you can check if your applications are working properly by referring to the instructions in Appendix A. Some applications (Skype, WINE and OSS applications) require manual configuration to work correctly - those are detailed in Appendix C.

---

### Post by markbuntu on 2009-04-30
One thing that can cause crackling is if the pcm volume in the alsa mixer is turned down. many people report that turning pcm volume al the way up fixes crackling. Some others report having to keep it below 80% or so to prevent crackling. Your results may vary.

There are some issues with the snd-hda-intel driver and pulse in jaunty but updates are on the way.

---

### Post by Jive Turkey on 2009-05-01
> **psyke83 said:**
> Please see my guide on PulseAudio.

After following the steps, you can check if your applications are working properly by referring to the instructions in Appendix A. Some applications (Skype, WINE and OSS applications) require manual configuration to work correctly - those are detailed in Appendix C.

Thanks!  I decided a fresh install would be prudent before following the guide, I haven't installed the proprietary codecs yet as I thought they may have been the problem. thanks for the excellent howto!

PS- I needed to reboot after step 4 to get pavucontrol working, a logout might have worked too.

[quote=markbuntu  ]	

One thing that can cause crackling is if the pcm volume in the alsa mixer is turned down. many people report that turning pcm volume al the way up fixes crackling. Some others report having to keep it below 80% or so to prevent crackling. Your results may vary.

There are some issues with the snd-hda-intel driver and pulse in jaunty but updates are on the way. [/quote]

That's an interesting tip, however at the time the crackling was the only noise I had.  Anyway, its still miles better than the 64bit MSVista driver - ie LOUD popping noise when say, minimizing a window.  I'm scared it could fry the mobo.

SOLVED !

---

