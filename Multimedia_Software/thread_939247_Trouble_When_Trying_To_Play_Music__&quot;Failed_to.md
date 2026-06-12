---
title: "Trouble When Trying To Play Music:  &quot;Failed to connect stream: Invalid argument&quot;"
date: 2008-10-05
forum: Multimedia Software
---

### Post by NuNn DaDdY on 2008-10-05
This issue just developed itself recently and I'm unsure as to what the problem is.  I recently installed wine but I don't think that should have caused the issue.  Also I installed the Java Environment so that may have contributed.  Any help would be appreciated. Thanks

---

### Post by pah99 on 2008-10-06
I also have the exact same error. This happens in Totem, Rythmbox, Mplayer, and Amarok. The only player that works is VLC. This is the terminal output from Totem:
pasha@pasha-laptop:~/Music/Russian/Rock/Lumen/Svoboda$ totem Detki.mp3
** Message: Error: Failed to connect stream: Invalid argument
pulsesink.c(487): gst_pulsesink_prepare (): /play/abin/audiosinkbin/audio-sink/bin4/autoaudiosink1/autoaudiosink1-actual-sink-pulse

When I first installed Ibex, I installed the mp3 codecs and everything worked fine. Then I went and installed a bunch of other stuff, including other codecs. After this it stopped working. In another post it was mentioned that the Dirac BBC codec caused problems, so I uninstalled it, and I still have this problem. So, Not sure what's going on. 

Does anyone know what is going on, or is this just a bug in Ibex?

---

### Post by Moog on 2008-10-07
> **pah99 said:**
> I also have the exact same error. This happens in Totem, Rythmbox, Mplayer, and Amarok. The only player that works is VLC. This is the terminal output from Totem:
pasha@pasha-laptop:~/Music/Russian/Rock/Lumen/Svoboda$ totem Detki.mp3
** Message: Error: Failed to connect stream: Invalid argument
pulsesink.c(487): gst_pulsesink_prepare (): /play/abin/audiosinkbin/audio-sink/bin4/autoaudiosink1/autoaudiosink1-actual-sink-pulse

When I first installed Ibex, I installed the mp3 codecs and everything worked fine. Then I went and installed a bunch of other stuff, including other codecs. After this it stopped working. In another post it was mentioned that the Dirac BBC codec caused problems, so I uninstalled it, and I still have this problem. So, Not sure what's going on. 

Does anyone know what is going on, or is this just a bug in Ibex?

Same here. Bug in Ibex. Specifically... the last kernel update. 
I think there must be an incompatibility with it and pulse. 

You can boot into the previous kernel via the grub menu to confirm this.

I have had this with another kernel upgrade (around 3 revisions back).

You could always file a report at launchpad, but before I could do it last time, a kernel upgrade fixed the issue.

That's the beauty of Beta's.

---

### Post by pah99 on 2008-10-07
I tried an older kernel, but it didn't work. I am currently using 2.6.27-5-generic. I tried 2.6.27-4. So, the kernel doesn't seem to be the problem, at least for me.

---

### Post by pah99 on 2008-10-07
I have updated to 2.6.27-6-generic. Still no luck.

---

### Post by Moog on 2008-10-08
GOOD NEWS,

Playback has returned this morning (UK) with an update to pulse audio and the pulse hal module.

I still think it was a kernel incompatibility with pulse.

Hopefully it's back for you too.

---

### Post by pah99 on 2008-10-08
I have updated twice today(morning and afternoon) and still no luck.

---

### Post by Moog on 2008-10-08
Aaaghh,

It's gone again after the recent updates. OSS works in System -> Preferences -> Sound but this doesn't help with streaming flash video.

Oh well. Roll on the RC on the 23rd, asnd if that fails the 30th for the full release.

---

### Post by pah99 on 2008-10-10
The latest kernel update has fixed this for me. I also have flash working correctly with sound.

---

### Post by ArgusVision on 2008-10-30
I'm having the same problem in 8.04. Kernel updates have not fixed it. I don't suppose something like apt-get update pulse would work?
 The kinda' strange thing is it is only doing this on my laptop, not my desktop or my wife's laptop. It might be a different app I have installed or hardware differences relating to the kernel.
I'm open to suggestions.

  Gonna' search forums and launchpad a little more and post any fix (or a link to the fix)I may find back here.

---

### Post by ArgusVision on 2008-10-30
Hey,

   Didn't find any answers in forums, but did think of something kinda' simple.  

   Went to System >Preferences >Sound and changed the "Music and Movies" setting from "Autodetect" to "ALSA" and guess what...
It worked. 

   Sometimes its the simple things...

Hope this helps someone.

---

### Post by pah99 on 2008-11-04
ArgusVision have you updated to 8.10? If so, has it fixed it for you? After the final version came out I stopped having the problem. So if you still have that problem, try upgrading.

---

### Post by JohQ on 2008-11-04
Thanks ArgusVision, your "trick" worked fine for me :)

For Amarok users (as myself), you have to go to Settings -> configure amarok -> engine -> change Output plugin from Autodetect to the one you prefer using.

---

### Post by naniekso2 on 2008-11-13
Thanks It Worked!

---

