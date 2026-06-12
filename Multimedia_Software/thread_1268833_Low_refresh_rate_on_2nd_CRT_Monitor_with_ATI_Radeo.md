---
title: "Low refresh rate on 2nd CRT Monitor with ATI Radeon HD 3650"
date: 2009-09-17
forum: Multimedia Software
---

### Post by quser on 2009-09-17
I'm having an issue with not being allowed to set a refresh rate above 60Hz on the 2nd monitor of my video card with Catalyst Control Center.  What I would like is to have both monitors working at 1280x1024 @ 85Hz with Xinerama.  All I need to acheive this is for the 2nd monitor to be at 85Hz instead of 60Hz.

Video Card:  Asus EAH 3650 Silent, ATI Radeon HD 3650 graphics engine
OS:  Ubuntu 9.04 64-bit, all updates complete
Video Drivers:  ATI Catalyst 9.9 (latest from ATI website)
Displays:  Dell P991 and ViewSonic G90fb (CRT displays, both connected with DVI to VGA adapters)

When originally trying to set up dual displays, I used the proprietary ATI/AMD FGLRX drivers installed through "Hardware Drivers" in ubuntu, but I could never get the displays set up properly, or get Xinerama to turn on.  However, I was able to set either display to 1280x1024 @ 85Hz if I messed with things in the right way, but never simultaneously as non-cloned displays.  In any event, nothing ever seemed to work consistently.

So I installed the drivers directly from the AMD website ([http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)), and everything works much more like it should, with the exception that I am not given the option to set the 2nd monitor to a refresh rate higher than 60Hz.  I've tried adding Modes to the xorg.conf, but whatever things I've tried with xorg.conf either seem to be ignored, or prevent X from running.

Also, the 2nd monitor never seems to be detected in the proper way.  In Catalyst Control Center, if I click on "Analog Monitor (1)", it will properly identify the display model, say that the max refresh is 85Hz, and identify the connector as VGA.  When I click on "Analog Monitor (2)", it identifies the monitor as only "Default Monitor", says the max refresh is 60Hz, and identifies teh connector as DVI.  It does not matter which monitor I have connected to which video port, the 1st monitor model is correctly identified and works fine, and the 2nd always is forced to operate at 60Hz or below (I think the two other refresh rates allowed are 43 and 46).

If I had LCD's this wouldn't be an issue, but I won't be doing that (so don't suggest it).  I prefer CRT's, and don't think I should have to buy new monitors just because my video card doesn't do what it should.

It is unfortunate that it is so difficult to get video to do what you want in linux.  I dream of the day it comes close to being as easy as Windows (but otherwise I find Windows almost unusable).

Thanks to anyone who can help.

---

### Post by markbuntu on 2009-09-17
Have you filed a bug report about this at the ati bugzilla. They may be unaware of this behavior. They test a lot but cannot possibly test every combination.

---

### Post by quser on 2009-09-17
No I have not, but I'll go ahead and do that.  But I hope someone here knows a way that may fix this before having to wait for a new release (this last one just came out a week ago).  The 60Hz refresh really gives me a headache, sometimes I find myself just shutting off the 2nd monitor so I don't have to see the flicker in the corner of my eye.

I actually notice my eyes are more sensitive to things flickering (anything, not just crappy monitors) when I view the flickering at the edge of my sight.  So this makes the 2nd monitor especially irritating since I'm spending most of my time looking at the higher refresh rate monitor.  I think this may have something to do with our animal instincts to observe movement with our peripheral vision.  I also notice my peripheral vision is better at night vision...  Anyway, this has nothing to do with my computer...

---

### Post by quser on 2009-09-18
This is something I really need to get working.

I will PayPal $10.00 (USD) to the first person who has the solution to this problem (hopefully this is not against any forum rules, I didn't see anything that would indicate this).  If this requires private communication outside the forum that is fine, but I will post the solution if I ever find one.

---

### Post by quser on 2009-09-20
Make that $15.

---

### Post by Raydan on 2010-01-12
Similar trouble: I've got 2 CRT monitors, connected to Radeon HD4350 by DSUB and DVI (via DSUB-DVI adapter) and both supporting more than 60Hz refresh rate at 1024x768. Monitor, connected to DVI always have max 60Hz, doesn't matter what monitor is it and how is xorg.conf configured. Tried both open source and proprietary drivers -- same trouble. 

Also it doesn't *seem* to be an adapter limit -- until KDM screen appears (i.e. bios screen, grub screen, kubuntu splash screen), DVI monitor *seem* to have good refresh rate.

---

### Post by Raydan on 2010-01-12
Hm, don't know what it was, but now DVI monitor refresh rate looks great. As I remember, the only thing that I did was replugging monitors there and back again. In KDE screen settings monitor has rates up to 85Hz at 1024x768, as it should, but ATI Control Panel still think that 60Hz is a limit. In xorg.conf DVI monitor section "TargetRefresh" parameter is "85", but until replugging (or something else what I've done but haven't noticed) this setting was ignored.

Really don't know what happened, but now everything seems fine.

---

