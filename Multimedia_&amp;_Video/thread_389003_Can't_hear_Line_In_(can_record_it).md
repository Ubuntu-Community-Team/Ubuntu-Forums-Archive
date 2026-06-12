---
title: "Can't hear Line In (can record it)"
date: 2007-03-20
forum: Multimedia &amp; Video
---

### Post by H3g3m0n on 2007-03-20
I want to hear the Audio from Line In from my speakers but it doesn't seem to want to come out.

I can record in Audacity and play the recorded sound back without issues but I can't find a way to pipe the audio directly out. I looked in the alsamixer, gnome-volume-control, kmix and unmuted the LineIN and set Capture1 to Line In but i can't hear anything.

I've tried unmuting everything and turning it all up. But no luck.

I tried to setup a basic software audio passthrough with "arecord | aplay", I can just about hear some sound, but it is way to quiet, it sounds more like radio interference being picked up from another input. It is deffinatly the sound from the game (xbox is the sound source). It might be its selecting the Mic port instead of the line in and the mic boost (turning it off stops the sound completely) is picking up the electronic interference from the line in and making it just audiable, but i don't know how to specify line in with arecord.

It works in windows, so I know its not hardware.

---

### Post by djen9999 on 2007-03-20
Go to >Edit>Preferences and click on Software Play through.  That might fix it.

---

### Post by H3g3m0n on 2007-03-21
Unfortunately that option doesn't appear in gnome mixer, its just a list of devices i can set to be visible (there all enabled).

EDIT: The option is in audacity but it stutters, I also would prefer not having to run audacity just to get the sound through.

---

### Post by themightychris on 2007-03-30
Hey I just found your post looking for a solution to the same problem and after some messing around I found something that fixes mine.

In gnome volume control, go to Edit->Preferences and enable the "Analog Mix" track, then crank that sucker up!

---

