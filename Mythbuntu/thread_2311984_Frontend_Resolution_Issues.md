---
title: "Frontend Resolution Issues"
date: 2016-01-31
forum: Mythbuntu
---

### Post by Digicrat on 2016-01-31
I have a dual (well, now triple) boot system with Win7,Win10 and Linux and a tri-monitor setup.  Both OS' have the same hostname, and each have a mythfrontend installed.  It has an AMD/ATI Radeon 5850 video card.  Originally, everything worked fine.

Then, one day, myth crashed under Windows.  After that, no matter what I did, I had issues watching videos in mythfrontend under EITHER OS.  Both the frontend and the UI would open on the correct (center) monitor, but was offset such that only half the video was visible on the screen.  I've abandoned the Win7 install for now, though eventually I may try again in Win10 so I can watch TV while working in either OS.  

Under Linux, I recently made progress by changing the LocalHostName in my config.xml file to be a unique value.  Now, instead of being off-center, mythfrontend simply thinks my screen is 1024x768 resolution, and the video/GUI only takes up a fraction of the screen.  It will also always load on whichever monitor is active, meaning I have to be careful to use a terminal or Run dialog from the center screen to even get it on the right monitor.  

I've tried passing in a "-geometry 1920x1080" flag when starting mythfrontend.  This does force it to use the correct resolution, but the GUI becomes stretched across 2 monitors (the side ones are older 1280x1024 screens).


Any ideas on how to get this back to a working state?

---

### Post by Digicrat on 2016-01-31
I seem to have found a (non-intuitive) resolution to my own problem.

Under Setup->Appearance->Screen Settings I changed the default display from "0" to "1".  

Apparently the MythFrontend is ignoring this setting and always spawning on the active monitor, BUT is taking the screen resolution from the selected value.  

As for why my right monitor (DVI) won't go higher than 1024x768 while my identical left (DisplayPort->VGA) is at 1280x1024; that is a battle for another day.  (For reference, my center 1080p display is DVI->HDMI).  

EDIT: Actually, I now recall that I settled for keeping the right monitor at a lower resolution because the radeon Linux driver apparently won't support a higher combined resolution on this machine, despite Windows having no issues.

---

