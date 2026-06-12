---
title: "HD output slightly choppy"
date: 2008-04-07
forum: Mythbuntu
---

### Post by whosmatt on 2008-04-07
Hardware:

P4 3.0 GHz
768MB RAM
PCHDTV 5500
ATI Radeon X300

I'm using VGA out to my tv @ 1280x768 (that's what the TV reports, anyway)
Picture is beautiful, however, in fast action (basketball, anything that pans side to side quickly) the picture doesn't look nearly as smooth as just using the TV tuner.  I'm using kernel de-interlacing option in Myth's tv settings.

CPU usage is high, but not maxed during HD viewing.

Is there anything I can do or should I just suck it up and buy a cheap Nvidia card?

FYI I'm using the open-source ATI driver as the proprietary one gave me an unusable resolution to the TV, and I didn't have the patience to try and troubleshoot.

Thanks for the hlep!

---

### Post by laga on 2008-04-07
> **whosmatt said:**
> Hardware:
I'm using kernel de-interlacing option in Myth's tv settings.


Try the 'bob' deinterlacer. Or one of the other 2x deinterlacers, eg greedyh2x oder yadif2x (which are new in MythTV 0.21). Although these use a lot of CPU, so it might not work if you play HDTV.

---

### Post by whosmatt on 2008-04-07
> **laga said:**
> Try the 'bob' deinterlacer. Or one of the other 2x deinterlacers, eg greedyh2x oder yadif2x (which are new in MythTV 0.21). Although these use a lot of CPU, so it might not work if you play HDTV.

Will do.  I realize I should have put this in my original post, but i'm still running 0.20.2.  I had a bad experience upgrading to 0.21via apt.

Edit:  Also, I should probably clarify that the interlacing doesn't seem to be the problem, it's more like a frame-rate thing.

---

