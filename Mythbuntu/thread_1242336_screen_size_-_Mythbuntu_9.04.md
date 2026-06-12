---
title: "screen size - Mythbuntu 9.04"
date: 2009-08-17
forum: Mythbuntu
---

### Post by HW_Hack on 2009-08-17
OK - basically everything is working but there are a few minor tweaks needed. I'm running a combo setup connected to a projection TV (vintage 2002) via SVIDEO. The TV has a 16:9 aspect ratio.

But the image being sent is too large - it is centered but the top-bottom and edges are not visible. In any of the Myth setup screens I can not see the bottom choice text boxes.

On the Ubuntu desktop (using the Nvidia app) the screen res is 1024x768 which appears to be max. I assume I need to go somewhere in the Myth setup files or x-window files and make a tweak.

Can I get any pointers on this ? Thanks

---

### Post by silverdulcet on 2009-08-17
If you are only concerned about the mythtv interface, then just go to Utilities/Setup>Setup>Screen Setup Wizards. Then just follow the instructions. There should be arrows in the upper left and lower right corners that you can adjust so they are visible on the screen. these define where the edge of the screen are for the mythtv menu. If you are unhappy with how it turns out, you can always go back into that menu and reset it. 

On the other hand, if you want to fix it for the entire desktop you need to find the option for adjusting overscan in the configuration for your video drivers. Either the nvidia control panel or the ATI/AMD one.

---

