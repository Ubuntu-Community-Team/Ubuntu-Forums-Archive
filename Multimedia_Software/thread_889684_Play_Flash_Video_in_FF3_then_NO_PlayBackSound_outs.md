---
title: "Play Flash Video in FF3 then NO PlayBack/Sound outside of FF3"
date: 2008-08-14
forum: Multimedia Software
---

### Post by ghetto2ivy on 2008-08-14
After I play a flash video in ff3 (youtube or vimeo or any), nothing else that plays video or sound works until I kill firefox. Quitting firefox allows all the videos to play. By not works I mean that video playback slows to a glacial pace (if any) and pressing play on rhythmbox or banshee yields no sound, and no movement from the song progress indicators.

I've check for runaway processes, but there don't appear to be any. Restarting Firefox after playing a flash video fixes it, but needless to say I don't want to restart firefox everytime I play a youtube video.

Running Hardy on an newer ICH10 Chipset.

---

### Post by Hagbard_C on 2008-08-16
I have the same problem, restarting the system is the only way for me to start a song from rhythmbox after i have watched a video on youtube.com

---

### Post by stepdown on 2008-08-16
The only way I know to get around restarting is to kill the Firefox process, System>Administration>System Monitor and then go to processes.

---

### Post by Hagbard_C on 2008-08-16
yeah thanks figured that one out to

---

### Post by ghetto2ivy on 2008-08-17
Hagbard_C, stepdown,

What version of Ubuntu are you using? How about your motherboards?

I ask because this only started once I switched motherboard & CPU -- so I suspect that has a lot to do with it. I had been using an Asrock 775 Dual VSTA motherboard, now I, using an ASUS PQ5LE.

---

### Post by psyke83 on 2008-08-17
It's a PulseAudio misconfiguration you're suffering. See: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) for a detailed explanation, and following the right breadcrumbs will get you Flash 10 RC installed with the proper configuration in place.

---

### Post by Hagbard_C on 2008-08-18
> **psyke83 said:**
> It's a PulseAudio misconfiguration you're suffering. See: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) for a detailed explanation, and following the right breadcrumbs will get you Flash 10 RC installed with the proper configuration in place.

This fixed it, thanks a bunch! now i can switch between youtube and rhythmbox fine! super! Thanks

---

