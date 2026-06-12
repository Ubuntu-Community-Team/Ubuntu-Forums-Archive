---
title: "How to properly update"
date: 2011-04-26
forum: Mythbuntu
---

### Post by phroman on 2011-04-26
Hello all, unfortunately I'm a bit confused about the process of updating my system, these questions might sound dumb, but I have to ask.. 

I read this in the wiki: 

> MythTV is designed as a PVR appliance, first and foremost. Once it is working, it should be hands off, even for what seems the most innocent of upgrades.  It may sound simple and foolish, but many people will tell you that once you have your MythTV system working, don't upgrade anything other than the MythTV application unless you absolutely have to.


How do I only upgrade the mythtv application, and not the rest of my system?  It seems like every time I turn on my computer there's that gray arrow in the tool bar notifying me of updates.  I'm not supposed to run any of those updates?  What about security updates?  Should I run System > Administration > Update Manager and just deselect everything else?  In Mythbuntu > Control Center I have .024 PPA selected, but why is there also a System Updates section in there if we're not supposed to update the system?  

I've been using Mythbuntu for about two years now, I've never had a system that was 100% working, but let's say I've been at 85%.  I've only had that level of operation solid for about a two month timespan, then something broke.  I've been updating everything all the time, and that's probably why, eh?

I think I'm going to do a fresh install, and would love not to mess this one up... :wink: 


Well, thanks for any advice and help on this, I appreciate it, cheers.

---

### Post by tgm4883 on 2011-04-26
> **phroman said:**
> Hello all, unfortunately I'm a bit confused about the process of updating my system, these questions might sound dumb, but I have to ask.. 

I read this in the wiki: 




How do I only upgrade the mythtv application, and not the rest of my system?  It seems like every time I turn on my computer there's that gray arrow in the tool bar notifying me of updates.  I'm not supposed to run any of those updates?  What about security updates?  Should I run System > Administration > Update Manager and just deselect everything else?  In Mythbuntu > Control Center I have .024 PPA selected, but why is there also a System Updates section in there if we're not supposed to update the system?  

I've been using Mythbuntu for about two years now, I've never had a system that was 100% working, but let's say I've been at 85%.  I've only had that level of operation solid for about a two month timespan, then something broke.  I've been updating everything all the time, and that's probably why, eh?

I think I'm going to do a fresh install, and would love not to mess this one up... :wink: 


Well, thanks for any advice and help on this, I appreciate it, cheers.


I'm of the rule, update everything available to your release, but don't install what you don't need.

ie. Do all of the updates in update-manager, but don't upgrade releases (eg. 10.04 to 10.10)

---

### Post by phroman on 2011-04-26
keeping things to a minimum seems like a pretty good idea, thx.

---

### Post by Bucky Ball on 2011-04-26
10.04 LTS most stable and the current long-term support release.

---

### Post by agamotto on 2011-04-28
In my experience, I only use LTS versions these days.  This helps quite a bit with unexpected 'fun.'  Go ahead and allow your *buntu system fetch the security updates and install in the background.  I tend to save all other updates for a monthly/bi-monthly session.  This eliminates the seeming weekly kernel patches/updates,etc...  Delaying in this manner eliminates some of the x.x.1 to .x.x.2 updates that other users seem to find so annoying.  Other than that, once you have the system the way you want, do an image of it for redundancy, then use it as you see fit.

Hope some of this helps!

---

### Post by phroman on 2011-04-28
It does!  Thanks everyone for your input and advice.  :)

---

### Post by phroman on 2011-04-29
> **agamotto said:**
> In my experience, I only use LTS versions these days.  This helps quite a bit with unexpected 'fun.'  Go ahead and allow your *buntu system fetch the security updates and install in the background.  I tend to save all other updates for a monthly/bi-monthly session.  This eliminates the seeming weekly kernel patches/updates,etc...  Delaying in this manner eliminates some of the x.x.1 to .x.x.2 updates that other users seem to find so annoying.  Other than that, once you have the system the way you want, do an image of it for redundancy, then use it as you see fit.

Hope some of this helps!

What's your current disk image creator of choice?  I'm looking at fsarchiver right now.

---

### Post by LowSky on 2011-04-29
I click yes to every update and upgrade. Heck I just did a 10.04 > 10.10 > 11.04 update just this week.

---

