---
title: "WICD in the Unity Indicator Applet?"
date: 2011-03-29
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by pivotraze on 2011-03-29
A while I ago, I installed WICD and removed Network-Manager.

Is there a way to get the WICD notification agent to appear where the time, volume, and battery thing is in unity?

Thanks in advance... Cody

---

### Post by mc4man on 2011-03-29
If they wrote in up to be in appindicators would be one way, thats up to wicd

IF wicd used to show in the the notification area, (only used once here a long time ago), then you could try adding to the systray whitelist and see what happens.
It may work fine, somewhat or not at all. It may or may not affect other things like the unity launcher. You'd have to ck, test and see.
Easy to add thru either gsettings in terminal or directly in dconf-editor

(an interesting thing about the 'systray area', is while it and any icons appear in the unity panel left of the indicators, they also seem to be 'on the desktop' to some extent.

---

