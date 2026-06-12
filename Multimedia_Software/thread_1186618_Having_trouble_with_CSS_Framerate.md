---
title: "Having trouble with CS:S Framerate"
date: 2009-06-13
forum: Multimedia Software
---

### Post by MysteriousKnight on 2009-06-13
I recently moved to ubuntu, after updating for 9hours, i now have 9.04
anyway, i installed steam using wine, updated it, and copied my updated Counterstrike source gamefiles over to the steam on my virtual c drive.

It plays, sounds great, but even set at lowest graphic settings (except the resolution), i get a frame rate of 11-27 and whenever a enemy enters the screen, i lag soooo bad.

I tried messing with the opengl setings, got a slight improvement. I do not have any other windows emulation installed.

My system specs are: AMD X2 64 5200+ 2.7GHz(clocked to 3.1)
3Gb DDR2 800 RAM
nvidia 8600GT 512MB DDR2

Please help because i want to get rid of MS WINXP for GOOD :(

---

### Post by MysteriousKnight on 2009-06-14
Oky, i got some performance increase by disabling the In-Game community, and setting wine to windows 2000, but i still have to play it at low quality to get a frame rate just above 30fps, wich is perfectly playable but i would like to have it at medium settings, my pc can take it on high in XP.

Not going to use windows to play it tho, lol, actually i think i'm going to format my Windows partition, lol

---

### Post by gotsanity on 2009-06-17
have you tried setting your debug messages to show none? thats a big slow down in most games in wine

run the following:

```
WINEDEBUG=-all wine "C:\Program Files\Steam\Steam.exe"
```

---

