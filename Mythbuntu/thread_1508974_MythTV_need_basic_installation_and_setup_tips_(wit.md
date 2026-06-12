---
title: "MythTV: need basic installation and setup tips (with Lucid)"
date: 2010-06-13
forum: Mythbuntu
---

### Post by boombox1387 on 2010-06-13
So here's the deal:  I have a SiliconDust HDHomeRun network tuner that works beautifully with MythTv (the standalone backend/frontend with Gnome, not Mythbuntu... sorry if I shouldn't be posting this here).  Over the past 4 months or so, I've had a setup that worked - with minor flaws - with Karmic.  I finally did a clean install of Lucid, and I'm getting ready to reinstall MythTv, but I'm hoping to do it in a way that avoids some of those little problems from last time.  Here's what was imperfect last time, which I want to avoid:

- I had some minor issues with the mythtv user that is automatically created.  Because this user is always logged in, it was impossible to shutdown the computer without an admin password, because there were "other users" logged in.  Is this normal? necessary?  This was probably my biggest annoyance with my last setup, and I'd love to avoid it this time if possible.

- The frontend didn't cover my panel (I have only a top panel... I use a dock at the bottom).  I worked around this by setting the panel to auto-hide, but it would be nice to avoid this if it's possible.

- The backend was always started when the computer started up, but for some reason I was never able to tune any channels until I had restarted the backend.  Without more information, I doubt anyone can help me with this one.  Hopefully this won't be a problem when I reinstall.

- Because my tuner is a network tuner, it has a network address which MythTv uses to locate it.  Sometimes this address changes (seemingly without rhyme or reason), and I have to reconfigure the backend because the tuner can no longer be found.  I'm guessing that this is something I'd need to change with my router, but if anyone knows of a workaround from within Myth, that would be appreciated.


Sorry this is sort of a "hey, come fix all of my problems!" thread, but I've been poking around the forums and mailing lists for a little while, and these are my unanswered questions.  If anyone has advice, particularly regarding the first two issues, I'll be very grateful.

---

### Post by superm1 on 2010-06-14
> **boombox1387 said:**
> So here's the deal:  I have a SiliconDust HDHomeRun network tuner that works beautifully with MythTv (the standalone backend/frontend with Gnome, not Mythbuntu... sorry if I shouldn't be posting this here).  Over the past 4 months or so, I've had a setup that worked - with minor flaws - with Karmic.  I finally did a clean install of Lucid, and I'm getting ready to reinstall MythTv, but I'm hoping to do it in a way that avoids some of those little problems from last time.  Here's what was imperfect last time, which I want to avoid:

- I had some minor issues with the mythtv user that is automatically created.  Because this user is always logged in, it was impossible to shutdown the computer without an admin password, because there were "other users" logged in.  Is this normal? necessary?  This was probably my biggest annoyance with my last setup, and I'd love to avoid it this time if possible.


This was a bug exclusive to using mythtv with gnome.  Didn't happen in XFCE.  It has been fixed though for Ubuntu 10.04 LTS.

> 
- The frontend didn't cover my panel (I have only a top panel... I use a dock at the bottom).  I worked around this by setting the panel to auto-hide, but it would be nice to avoid this if it's possible.

This will happen if you had desktop effects on.  You can work around it by either turning off desktop effects or installing the compiz settings manager and turning on the setting to not apply effects to full screen windows.

> 
- The backend was always started when the computer started up, but for some reason I was never able to tune any channels until I had restarted the backend.  Without more information, I doubt anyone can help me with this one.  Hopefully this won't be a problem when I reinstall.

Probably a racy condition with Network Manager and Myth backend.  I think this behavior is improved in 10.04's mythtv, but you'll see.

> 
- Because my tuner is a network tuner, it has a network address which MythTv uses to locate it.  Sometimes this address changes (seemingly without rhyme or reason), and I have to reconfigure the backend because the tuner can no longer be found.  I'm guessing that this is something I'd need to change with my router, but if anyone knows of a workaround from within Myth, that would be appreciated.

The serial number of the device shouldn't change - and this is what is used to contact it on the network usually.  (Myth doesn't keep that cached internally afaik).

> 
Sorry this is sort of a "hey, come fix all of my problems!" thread, but I've been poking around the forums and mailing lists for a little while, and these are my unanswered questions.  If anyone has advice, particularly regarding the first two issues, I'll be very grateful.

I'd recommend going for it and see what happens.  If you are still having issues, go activate auto-builds to get the latest 0.23 bug fixex ([http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds)).  They'll work on any *buntu, you don't need to be running a mythbuntu live cd based install.

---

### Post by boombox1387 on 2010-06-14
> **superm1 said:**
> 
I'd recommend going for it and see what happens.  If you are still having issues, go activate auto-builds to get the latest 0.23 bug fixex ([http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds)).  They'll work on any *buntu, you don't need to be running a mythbuntu live cd based install.

Thanks for a very helpful, thorough response! I ended up just going for it, and was pleasantly surprised to find my first issue fixed.  After a little more digging, I also found [this launchpad bug report]("https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/348934") that addresses my second issue.  Also, thanks for the explanations on questions 3 and 4.  Neither of these have been issues so far, so... fingers crossed.

All in all, my MythTv experience wasn't bad with Karmic, and it already seems a lot better with Lucid.  Yay!

---

