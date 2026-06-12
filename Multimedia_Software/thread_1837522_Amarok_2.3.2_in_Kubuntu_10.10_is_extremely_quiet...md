---
title: "Amarok 2.3.2 in Kubuntu 10.10 is extremely quiet..."
date: 2011-09-01
forum: Multimedia Software
---

### Post by lparsons42 on 2011-09-01
I am running Kubuntu 10.10 on my laptop, and the sound works fine in firefox (flash video, etc).  However Amarok is so quiet that I can barely hear it at all.  I have every volume adjustment I can find turned all the way up and I have to put my ear right next to the speaker to hear anything at all; any further away and I wouldn't even know it was on.

At first I thought it was just when listening to streaming music, but I tried an mp3 that I know the volume of and I have the same problem with it.  

What else effects the volume in Amarok?  My system sounds (startup and shutdown sounds) are fine as well.  I also went to "system settings" -> multimedia -> phonon -> audio output -> music and tested the sound card there, the volume was fine there too.  Only one sound device is listed there.

---

### Post by lparsons42 on 2011-09-01
After poking around a little more, and finding more people who have had the same problem and not found an answer, I saw one person mention rhythmbox.  I installed that and found the volume works correctly on there, so at least I can listen to some music while trying to figure out what is wrong with amarok.  I did have to install some additional plugins for rhythmbox to be able to play mp3 and internet radio (gstreamer and related) but at least it works.

---

### Post by lparsons42 on 2011-09-02
I found that after installing the plugins (gstreamer and associates) for rhythmbox to play mp3 and streaming internet radio, amarok now plays at an audible volume.  

Frustratingly, however, I have no idea what module made the difference for amarok.  The xine modules that are most often mentioned as being the culprits for this situation where already installed properly prior to my installation of rhythmbox, so it should have been something else.  

At any rate, I guess we can mark this [solved].  My solution was:

*  Give up on amarok, install rhythmbox
*  Start rhythmbox, find that it doesn't play either
*  Install gstreamer plugins for mp3 and streaming audio playback
*  Restart rhythmbox, find that it works correctly
*  Restart amarok, find that it now works correctly as well

:-?

---

### Post by .... on 2011-09-02
It might have been the pulseaudio volume, as it has per-application volume control.

---

### Post by lparsons42 on 2011-09-05
> **.... said:**
> It might have been the pulseaudio volume, as it has per-application volume control.

I have heard that suggestion before but I was unable to find any pulseaudio settings that made any difference.  I also checked the files in /etc/pulse and ~/.pulse and found nothing that referred to amarok (or any application-specific volume settings).  

Hence as best I can tell it was something to do with a gstreamer dependency.  Which of course doesn't make much sense, unless that cleared up some sort of circular dependency while installing.  

Either way, amarok now plays at a volume that can be heard, so I'm happy.  Too bad I couldn't say that from the initial install.

---

