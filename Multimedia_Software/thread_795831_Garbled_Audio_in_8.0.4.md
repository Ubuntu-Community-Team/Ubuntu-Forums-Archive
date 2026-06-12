---
title: "Garbled Audio in 8.0.4"
date: 2008-05-15
forum: Multimedia Software
---

### Post by Justin Holland on 2008-05-15
I am in need of help and haven't found anything that directly relates to my problem.  I've just finished updating from 7.1.0 to 8.0.4.  I'm running it on my HP Pavilion DV6000 laptop.  Since I've updated that audio is totally screwed up.  The login, logout, and all other audio comes through the speakers all garbled.  What can I do to correct the problem?

-= Justin =-

P.S.  I'm not all that familiar with Ubuntu and Linux (only recently made the switch about 2 months back).  I've been a PC/Microsoft person since DOS 3.3.  I made the switch since I'm not about to use Vista due to the many issues with it (makes me think of the total flop of an OS with Windows Millennium Edition).

---

### Post by ubuntu-freak on 2008-05-15
Try explicitly selecting PulseAudio in System > Preferences > Sound, instead of Auto Detect. If there is no improvement, even after a reboot, switch to ALSA instead (Gutsy used ALSA). You will have to tell non-GNOME apps (VLC, MPlayer etc) that you are now using ALSA, which you can do in their preferences. Reboot if anything weird happens, then test again.
 
Nathan

---

### Post by Chubbymoth on 2008-10-05
I had a similar exerience. But it was after installing a load of software that my sound got garbled as if two drivers where competing at the same time for some memory.

I removed Pulse Audio and then ALSA and afterwards reinstalled both in the same order while making ALSA the default setting which seems to have been the solution for a short while. Apparantly though one of the apps is leaking into the same memory as the problem returned.

Is there a way to make sure that only one of the daimons is active apart from working through the process list? It can be Rythm box itself as well that&#347; the culprit, though the problem exists in every app :-(

It doesn matter wheter I use the NVidia Hal that is steering it or something like the OSS driver. The nasty bit is that it worked flawless, so apparantly I may have to dig into some config file (any clue which one that might be?) to dig up the problem and kill it.

---

