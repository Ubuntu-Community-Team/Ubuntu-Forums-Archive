---
title: "Can't use gamepad- also, potential fix for some people."
date: 2007-05-31
forum: Multimedia &amp; Video
---

### Post by DreamMastR on 2007-05-31
NOTE:  As explained below, many people are complaining they can't get their joystick axis to work in game.  THERE IS A BUG in Jscaliber.  Try using jscal.




Similar issues to this one have been posted many times, but no one seems to have a solution.

When trying to use either my PSX pad with USB converter (Green Asia developed Radioshack converter) or N64 Adaptoid I would only be able to use the buttons in game.  The control axis would work in Jscaliber, but wouldn't post in any games.

After many hours of searching, I read of a bug in Jscaliber, and someone suggested removing it and using jscal.  I did this, and lo and behold, my axis posted!

However, when I tried to play any actual game, the joystick axis was constantly posting as being pushed on the  y+, x+ axis.  In other words, my character, icon, etc. would constantly move down/right even when the analog joystick was in neutral.

It was then I noticed in jscal the gamepad would default to 127 when calibrating.  Moving the pad to the negative axis would bring the calibration to 0, and the positive axis would bring the pad to 255.

In other words, my axis are calibrating on a 0, 127, 255 spectrum, instead of -127, 0, 127.

Further troubleshooting revealed this to only be an issue with my PSX pad.  My N64 pad is now working (since I removed Jscaliber).

Any suggestions?

Your help is greatly appreciated.


UPDATE:  Right after posting this I remembered that I had a universal PS2 to Gamecube/XBOX/USB adapter a company had sent me several months ago as a freebie to make up for a mistaken order.  This adapter had the same issue, so possibly the issue lies in how the PS2 controller (DualShock 2) handles axis, and not the converter, as I would have initially suspected.

---

### Post by matemargo on 2007-06-05
Sounds like the solution to my problem.
I'll try this at home and give you some feedback.

---

### Post by matemargo on 2007-06-07
Yes! it worked perfectly.

---

### Post by DreamMastR on 2007-06-07
Thrilled I could help.  I feel like a real member of the community now (seriously).

---

