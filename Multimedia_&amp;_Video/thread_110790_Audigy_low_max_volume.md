---
title: "Audigy low max volume"
date: 2005-12-31
forum: Multimedia &amp; Video
---

### Post by borisattva on 2005-12-31
Strangely enough out of the 3 install attempts with absolutely no differnce in input from me the sound was sucessfgully recognized and began to work, albeit low.
I hear it fine and relatively loud, but not 'window-vibrating loud'.
The max volume is about 60% of what max used to be.

in win xp i had advanced options that would allow me to boost each channel (althought i did not even have to do that) In ubuntu, preferenced merely allow me to tweak which devices are available for volume adjustment.

Is there anything i can tweak to make the max be what it used to?

---

### Post by Zeroedout on 2005-12-31
try alsamixergui

---

### Post by borisattva on 2006-01-02
thanks for responding. 

i found something else though. I was chosing to use Rhythmbox as my music player, which only seems to manipulate the Master Volume.
When i loaded up XMMS, volume switch on that one adjusted the PCM, which turned out to have been set way low.

Stranger further, even seting the PCM to max, did not affect Rhythmbox master volume - its still subdued. So if i need to play music for a party i have to use XMMS and its lack of library control flexibility.

Atleast the mistery is solved.

---

### Post by borisattva on 2006-01-02
deleted

---

### Post by phii on 2006-06-05
Confirmed problem/solution.

I had the same problem, but i don't use XMMS so i had to open Gnome ALSA Mixer and there i found out that the PCM was set below half.

I guess you could also check/use alsamixer in your terminal.

Just wanted to confirm that this solved my issue altough I don't have XMMS.

---

