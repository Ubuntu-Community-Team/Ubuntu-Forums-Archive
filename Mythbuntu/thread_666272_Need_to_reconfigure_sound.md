---
title: "Need to reconfigure sound"
date: 2008-01-13
forum: Mythbuntu
---

### Post by Waistless on 2008-01-13
I've got some wierd things happening with my sound on mythbuntu, it appears I have 2 sliders which control it, PCM and "Front". If both are left on full, then the sound quality will degrade and sound muffled on lots of action, Bass sound. 

At first I thought it was a problem with the sound buffer, but the interesting thing though is If I turn either fully down, the sound will be mute, but if I turn PCM down to just 1, so it's barely on, and "Front" on full, it will result in flawless sound. However, the main volume control is PCM, so it just doesn't seem quite right having a sound volume adjust on my taskbar which appears to have the sound completely down.

The sound device is HDA Nvidia

Is there anyway I can reconfigure my sound to remain flawless but only use the main slider? Any help would be appreciated :)

---

### Post by racmar on 2008-01-18
you could try sshing to the machine or use a terminal and run a program called alsamixer.  alsamixer can easily control your sound output.  be sure to read the man page to see how it works.  Basically, use left, right, up and down. and press ESC to exit.  Also, don't let the "names" of the outputs fool you.  try changing these things while you are listening to something.

---

### Post by Waistless on 2008-01-18
Ahhh thanks, I figured out what it was

When PCM is set above 74, the result is a DB Gain above 0, and it corrupts the sound. Strangely though all other output sliders are limited at a DB Gain of 0, so perhaps an oversight?

For now though, I guess my problem is fixed :)

edit: [https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/42043](https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/42043)  This bug REALLY needs to be fixed.

---

