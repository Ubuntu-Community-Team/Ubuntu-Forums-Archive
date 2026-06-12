---
title: "[SOLVED] Fresh install of 8.10 on existing front+backend"
date: 2008-11-23
forum: Mythbuntu
---

### Post by Crusty Juggler on 2008-11-23
My Mythbuntu box has been operating reasonably well with only a couple of easy to fix (thanks to people here!) hiccups, so I'm not sure if I should upgrade or not.

My main concern is losing my recordings.  I have a / partition and a /var/lib partition on my HDD, so I assume that I can install 8.10 and in the partition manager, select the / partition to format and leave my /var/lib partition alone and have everything be okay.  Will this work?  I imagine a database rebuild may be in order, but that should be no problem.  

Is there anything I'm overlooking?

---

### Post by 86and96 on 2008-11-26
I tried that on an upgrade of 7.04 to 7.10, and the installer would not let me leave the /var partition without formatting it. I think that you will run into the same issue.

---

### Post by klc5555 on 2008-11-26
> **Crusty Juggler said:**
> My Mythbuntu box has been operating reasonably well with only a couple of easy to fix (thanks to people here!) hiccups, so I'm not sure if I should upgrade or not.

My main concern is losing my recordings.  I have a / partition and a /var/lib partition on my HDD, so I assume that I can install 8.10 and in the partition manager, select the / partition to format and leave my /var/lib partition alone and have everything be okay.  Will this work?  I imagine a database rebuild may be in order, but that should be no problem.  

Is there anything I'm overlooking?


Maybe just a good rationale for upgrading. If your Hardy machine is working smoothly, and in lieu of some new 8.10 feature that you just gotta gotta have, or a patch for something broken that is not likely ever to be backported to 8.04, why would you upgrade?   

On the down side, there is bound to be breakage of various sorts, and you will be moving to a version (8.10) whose service life (and patch availability) will expire _before_  8.04-LTS's does. On the other hand, the upside of the upgrade for you would be, well, what? :confused:

Just my $.02. At least be sure to back everything up before you leap from your solid stable system to the great beta-ish cutting edge.

All the best! :)

---

### Post by Crusty Juggler on 2008-11-27
In case anyone else is in the same boat, I'll put a bit of an update and mark this as solved.

The reason I wanted to update was for the updated network manager, as two separate wireless cards performed very poorly for me.  I ended up upgrading via the update GUI and everything went smoothly.  Almost.

The database was fine and recordings, videos and music were untouched.  My NVIDIA (177 beta, I think) driver failed, but that was okay because I wanted to put the 180 beta on anyway.

Wireless network has been great since, so I'm glad I did the update.

However, the one issue that I now have is that LIRC has stopped working.  My remote is detected and basic functions like enter and the number buttons work, but nothing else.  It's like it is not recognising my lircmd configuration.  

The remote worked perfectly before, and I have a topic buried on here somewhere that says how I got it working, but others have said that this method didn't work for them.  I'm wondering if it is an 8.10 issue...

---

