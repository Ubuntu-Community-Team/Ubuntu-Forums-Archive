---
title: "VLC playback error using EnvyNG"
date: 2008-08-24
forum: Multimedia Software
---

### Post by Blind Tiger on 2008-08-24
While running Gutsy, VLC worked flawlessly -- great quality, excellent control and response.  I used the restricted driver for my ATI X800 GTO.

I did a clean install of Hardy, installed VLC and required dependencies for dvd playback, and found video quality to be poor --stutters, poor resolution at full screen.  (still using the default restricted ati driver)

So I then decided to get the most recent driver using EnvyNG.  This then caused VLC to not function correctly.  When a dvd begins to play, it will flash the menu screen momentarily, then the screen/window goes black yet I continue to hear the soundtrack.  In full screen, the quality is back to what it was on Gutsy, but I cannot get playback to function properly in windowed mode.

-------update---------
After following this guide "[http://forum.compiz-fusion.org/showthread.php?t=6794]("http://forum.compiz-fusion.org/showthread.php?t=6794")", I now have windowed video playback in VLC, but there is a lot of flicker.

------update--------
A simple solution to this error is to disable Desktop Effects via right clicking the desktop, selecting Change Desktop Background, select the Visual Effects tab, then checking None.  This  will turn off Compiz rendering.  The flicker is due to direct rendering of the application in conflict with indirect rendering done by Compiz.  When finished using the needed application, just  re-enable effects, and compiz will be active again.

---

