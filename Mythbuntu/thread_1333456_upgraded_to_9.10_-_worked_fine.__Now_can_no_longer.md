---
title: "upgraded to 9.10 - worked fine.  Now can no longer login"
date: 2009-11-21
forum: Mythbuntu
---

### Post by Kereszte on 2009-11-21
Yesterday, I finished upgrading to Mthbuntu / Ubuntu 9.10 from 8.04.  After the installation, everything worked great and I was on my way to finishing up my dvd collection.

Last night, I started a dvd rip and went to bed.  When I got up, I noticed that the rip stopped at ~62% so I escaped out of it.  After that, I noticed that the dvd player would no longer play and my system was running slow so I restarted.

After restarting, I noticed that the system didn't automatically log me in like it used to so I tried to manually login.  When trying to login, I got a few screen blips and then was sent back to the login screen.

I did change my resolution yesterday, so I thought that may be the issue.  However, I was more concerned with my DVD player (if it had broke, etc).  So I logged in as root and tried to start the myth front end, it told me that I needed to be in the mythtv group so I allowed root to be added and restart the session.  When I started the myth front end, it wanted me to reconfigure everything from scratch, so I promptly exited.

From there, I searched my default user's home directory for a configuration file that may keep default x settings (per user)...  Didn't find anything so I decided to try another restart.

Upon restarting, I could not login with my default user and neither could I login with root...  (This leads me to believe that it is not an X windows issue.)

Searching other posts, I see that people with similar issues are experiencing it due to the myth backend not starting, but my messages log file does not suggest an error starting mythtv.  

What leaves me confused is why I could initially login as root, but can no longer do so...

Any help would be greatly appreciated.  I am not sure where to look from here.
AJ

---

### Post by colinnc on 2009-11-21
Have you verified that you haven't run out of disk space?

---

### Post by neutron68 on 2009-11-21
It sounds like you have the multiple-login problem.  There are a number of us who have seen this.  You may have to go through the login loop 10-20 times before it will finally let you in!

I started a thread in Installation and Upgrades on the topic:
[http://ubuntuforums.org/showthread.php?t=1320954](http://ubuntuforums.org/showthread.php?t=1320954)

I had the multiple-login problem, but no longer have it.  Last weekend, I did some experimenting and found that a change in the xorg.conf file seemed to fix it.  Another person found the same thing.  
If we are correct, the xorg.conf file needs to be revised from an "old format" to a "new format".  I posted my before (not working properly) and after (working) xorg.conf files.  If you look carefully, you can see that a number of things changed, such as denoting specific devices as "Device0" rather than "Configured Video Device", and "Screen0", rather than "Default Screen", and "Monitor0", rather than "Configured Monitor".

It would be good for Ubuntu and xorg experts to look over what we've found.  We may have found the basis for a fix.

If you get your system working by an xorg.conf update, post your before and after versions of the file so we can see if the change pattern holds true for you, too.

Eric

---

