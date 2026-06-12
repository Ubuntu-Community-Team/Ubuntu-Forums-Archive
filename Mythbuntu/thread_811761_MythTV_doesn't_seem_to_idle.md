---
title: "MythTV doesn't seem to idle"
date: 2008-05-29
forum: Mythbuntu
---

### Post by maeks84 on 2008-05-29
Hi,
I hope it's okay to post this here.  I'm not running Mythbuntu, but am running MythTV on a regular install of Ubuntu Hardy Heron.  Everything in the general area get buried so fast...

I'm running a combined backend/frontend.  I have a script written that should set the wake time for my motherboard, but for now, I'm not using it.  I just want MythTV to shutdown when not in use.  (Idle)  I'm being forced to shutdown, since I haven't been able to get my motherboard to wake from S3 or S4 at a set time.

My settings in Mythbackend setup are as follows
**Block shutdown before client connected:**  Unchecked
**Idle shutdown timeout:**  15
**Max. wait for recording:**  1
**Startup before rec.:**  210
**Wakeup time format:**  hh mm
**Command to set Wakeup Time:**  
**Server halt command:**  sudo shutdown -h -P now
**Pre Shutdown check-command:**  exit 0

Next scheduled recording is hours from now.  I've even logged in as root to see if permissions were the issue.  I've tried waiting for 15 sec at the frontend menu, at the desktop, and even at the login screen.  Nothing seems to work.  Any ideas?

---

### Post by maeks84 on 2008-05-29
Okay, figured this out,
I had edited my */etc/sudoers* file so that my user (not "mythtv") had the ability to do the necessary sudos without entering a password.  After checking the auth.log (found a reference to that in another post) there was a failure of user mythtv trying to sudo.  I didn't think I had a user mythtv.  Doesn't show up in Users & Groups.  Anyhow, gave mythtv the necessary permissions using visudo (that itself is a litte tricky to figure out) and it now works.  I have to quit Myth Frontend, but I'll work around that for now.

---

