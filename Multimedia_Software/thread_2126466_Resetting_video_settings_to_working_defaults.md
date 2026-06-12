---
title: "Resetting video settings to working defaults"
date: 2013-03-17
forum: Multimedia Software
---

### Post by Correctrix on 2013-03-17
Hi, I have Ubuntu Quantal on a Toshiba Satellite A100.  It was working just fine, and then I decided to install the game Beat Hazard Ultra, which failed.  When I rebooted, I realised that all 3D acceleration was off.  I couldn’t run any compositing window manager.  Unity with Compiz failed horribly.  I had to install KDE to be able to get a working desktop (KDE seems to degrade more gracefully in the event of compositing failure).

I’ve tried reinstalling a lot of packages, but it didn’t work.  What can I do to reset the video settings to what they were before the game messed with them?

OK, after lots of fiddling with things, I realised that all these nvidia packages are here for no reason.  I think that the game may even have installed them.  The laptop runs an Intel VGA.  I got rid of the Nvidia stuff and made it run mesa packages.

---

