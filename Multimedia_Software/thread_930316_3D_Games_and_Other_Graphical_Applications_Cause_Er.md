---
title: "3D Games and Other Graphical Applications Cause Erratic Flashing"
date: 2008-09-25
forum: Multimedia Software
---

### Post by jeffgriffin on 2008-09-25
Hello everyone. Sorry to start out my first post with a cry for help, but alas, I'm not having much luck. I have dug through the forums, but haven't found much in the way of insight on this problem.

I first noticed strange flashing whenever I clicked the mouse in Half-Life (running in Wine). I assumed this was a problem with Wine and disregarded it. It progressively got worse. I now notice it in all 3D Wine applications I run (as well as a few 2D ones, but Age of Empires 2 still hasn't experienced it). I began running in to it in non-Wine programs as well, such as GNUbik, glChess (w/ 3D enabled) and Alien Arena, none of which were run through Wine.


As for the flashing itself, it depends on the app. For example, in Half-Life the game would run perfectly until I clicked the left mouse button, which would cause a strange picture of the game's menu to pop up. Day of Defeat in Wine is not playble, as it flashes so much and disappers so much it gives me a headache to look at it (the only way to make this stop was to set the video render setting to "software", which was much too slow to be feasible). As far as non-Wine games go, GNUbik, Alien Arena and glChess are all unplayable since the in-game objects don't appear for more than 2-3 seconds before flashing white and disappearing, then coming back again.

My video hardware consists of an Intel x3100 GMA. I have 3GB's of RAM, a 1.86GHz processor, and my computer (a laptop) runs on the Centrino platform.

**Running Ubuntu 8.04 with latest updates.

---

### Post by Thingymebob on 2008-09-26
Turn off compiz, in a terminal type
metacity --replace

when you're done type
compiz --replace

or install the fusion-icon from the repositories which will appear in your notification area

---

### Post by jeffgriffin on 2008-09-27
**Slaps forehead**

I should have thought of doing this. Everything runs great now, thank you.

---

