---
title: "Upgrade from 9.04 to 9.10 cause mythtv issues"
date: 2010-07-27
forum: Mythbuntu
---

### Post by lofgren on 2010-07-27
Hey people,
I'm after some clues..
I upgraded from 9.04 to 9.10 over the weekend, upgrading mythtv from 0.21 to 0.22 in the process. 
Something went wrong and I have a few issues..

The box runs as a backend in a cupboard, but also has frontend installed for testing. I watch recorded TV in the lounge using XBMC 9.11. I don't plan to rebuild from scratch because, well, this is linux and I have other stuff running on that backend box.

Issue 1 - mythtv-database didn't configure properly during the install.
I noticed an entry on the terminal screen during the upgrade that mentioned mythtv-database and it suggested running "sudo dpkg-reconfigure mythtv-database".
Running that command only repeats the same suggestion.
I noticed a few packages were broken (mythtv-database and master-backend).

I have subsequently uninstalled all mythtv packages and reinstalled. Nothing lists as broken any further, but that message appeared again during the reinstall and I still get that error if I run "sudo dpkg-reconfigure mythtv-database".

I have confirmed that the debian-sys-maint password is correct by logging into the database with it ([http://ubuntuforums.org/showthread.php?t=1340244](http://ubuntuforums.org/showthread.php?t=1340244))

I did run myth frontend at that point and it did prompt for an initial configuration. Frontend *may* have updated the database as suggested it does in other posts, but I cannot confirm that. The schema version reported in mythfrontend.log is 1244. A quick search suggests that is correct for myth 0.22... so maybe it did?


Issue 2 - mythbackend.log isn't receiving any new events.
After the upgrade, I first uninstalled/reinstalled mythtv-backend and fixed a couple of minor errors. The last one at that point in time, was linking tuner cards to sources.
Since then there has not been an error or otherwise logged to mythbackend.log


Issue 3 - XBMC won't play videos recorded since the 0.22 upgrade.
Old videos we haven't yet watched/deleted play fine, but new ones leave an error in xbmc.log to the effect of not being found.
The frontend instance on the backend server plays new recordings. 
I can play the new videos from the backend smb share via the XBMC box. 
I have configured my myth:// source using IP in XBMC and I have a static entry in the hosts file ([http://wiki.xbmc.org/?title=MythTV#Recordings_Don.27t_Play](http://wiki.xbmc.org/?title=MythTV#Recordings_Don.27t_Play)). 
I have installed XBMC on an XP laptop and get the same behaviour..
So I am kinda stumped.

thanks,
Lofgren

---

