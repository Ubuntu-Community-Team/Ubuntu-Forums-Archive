---
title: "Blank screen, help!"
date: 2005-11-18
forum: Multimedia &amp; Video
---

### Post by CarbonPlexus on 2005-11-18
Alright my original problem was that 1280x1024 looked pixely and odd so I had to use 1024x768 or lower so everything rendered normally.  I wasn't sure if even though my ATI Radeon 7200 was detected in xorg.conf whether I needed to still install/reinstall an ATI driver.   Anyway while I was trying many different fixes for my display problem I saw a post with a config tool I was supposed to use instead of changing xorg.conf manually because they said it was "too dangerous".  Needless to say after going through the config tool and rebooting the GDM login thing won't come up anymore.  I finally realized after a few reboots that the GDM was running even though the screen was black so I was able to login by putting in my password and username though I couldn't see anything (not even the cursor)  Not only that but now even the screen at 1024x768 is rendered all pixely.  Could anyone tell me how to fix this so the GDM comes up properly?

---

### Post by CarbonPlexus on 2005-11-18
Ok I think I found part of the problem.  The background resolution (not the interface one) *sorry I'm a newb* I put at 1600x1200 which makes my screen go blank.  I realized this because I just tried putting the interface (Gnome) res at that and the screen went blank (luckily there's that thing that fixes the res back to normal if you don't push "accept resolution" after a few seconds.)  The problem is I can't seem to find the post that tells me what to change to fix the background resolution (perhaps if I knew the technical name I could search for it better?)  Any help would be appreciated.

---

### Post by CarbonPlexus on 2005-11-18
alright I found the tool to reconfigure my settings and I can now see the GDM again ^_^*so thankful*  But the high resolution still looks kinda odd (1280x1024) so any insight into that would be appreciated.

---

### Post by CarbonPlexus on 2005-11-19
Hmm funny thing happened... I took my computer home for break and now that I'm using a different CRT the 1280x1024 looks fine!  I'll be switching CRTs now that I know it's a hardware and not a software problem. But it's still odd how this CRT (same model as the other) works at 1280x1024 in both Linux and Windows but the other one only works at that res. in Windows...

---

