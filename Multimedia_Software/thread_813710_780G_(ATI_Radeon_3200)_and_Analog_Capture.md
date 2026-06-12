---
title: "780G (ATI Radeon 3200) and Analog Capture"
date: 2008-05-31
forum: Multimedia Software
---

### Post by smithfarm on 2008-05-31
I'm trying to get Analog Capture to work on the new Gigabyte board with the 780G chipset, using the proprietary driver from ATI. (flglv or something like that)

Kernel recognizes my TV card no problem. I'm getting the video signal from Composite Video 1. (mplayer tv:///1) When I run in single head configuration, I can see the video feed but it's choppy. When I switch to dual-head, it works. 

But for some reason, "it works" comes with a price: I lose window frames. When I open a window, it opens at the top left of the screen, has no title bar, can't be moved, can't be resized. When I go back to single-head, the window frames come back.

I will send the xorg.conf file later but I don't think that's where the problem is. Even when I just edit the dual-head xorg.conf file to remove the stanzas for the second screen, it just goes back to the "choppy video with window frames" mode.

Any input appreciated.

Nathan

---

