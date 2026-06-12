---
title: "Optimizing TV out with NVIDIA control panel"
date: 2009-11-08
forum: Mythbuntu
---

### Post by geolizardo on 2009-11-08
I have recently configured a fresh install of Mythbuntu 9.1.  I am using an NVIDIA 6400 card for the TV out.  I have the card working to the point I get video on both my VGA LCD as well as through the SVIDEO out to my 4:3 36" TV.  

The problem being, I'm not able to find a resolution setting that allows me to see the text on the TV screen effectively.  Part of the trouble is that I don't understand the invented words that NVIDIA has used in the control panel (Twinview?).

Here is how I have it:
Xserver Display configuration:

Model: Samsung SyncMaster (CRT-0 on GPU-0)
Configuration: TwinView
Resolution: 1024x768 -Auto Refresh
Position: Absolute  +0+0
This is the primary X Screen

Model: TV-0 (TV-0 on GPU-0)
Configuration: TwinView
Resolution: Auto (which shows as 1024x768 on the graphic display above)
Position: Absolute  +0+0

In the graphic view above, I have dropped one screen on top of the other and that seems to have me close to a solution, but the number of truncated words and entries on the Myth screens is bothersome.  And it certainly isn't that I have the font size set to large.  

So does anyone out there have a similar setup that they can relate their video setup to me?
Thanks.

---

### Post by kadafi69 on 2009-11-08
I have the same card, and the same problem, I've just learned to live with it. There doesnt seem to be any way of finding a suitable resolution. In the end I have just adjusted all the font settings and appearance settings till i got something I found acceptable.

---

### Post by schwinn on 2009-11-09
Do you mean to say that you are running into issues with overscan? That's a pretty common issue on these systems... I used nvidia-settings to change the overscan amount to get it all to line up properly... well, decently enough, that is. I don't use a dual-display, just the TV... and I can keep the text right at the very edge of the TV, though it certainly still clips a few lines all around... but it's very usable this way.

---

