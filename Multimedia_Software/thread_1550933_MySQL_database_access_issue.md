---
title: "MySQL database access issue"
date: 2010-08-11
forum: Multimedia Software
---

### Post by gtblackwell on 2010-08-11
I was having this issue with my Myth box a couple days ago and after a number of attempts to solve it, ended up reinstalling.  Originally, I had installed MythTV on an Ubuntu installation.  This time I opted for a MYTHbuntu installation with the ubuntu-desktop package installed afterward.  But to no avail.  Here's the issue:

Whenever I reboot my system, mythfrontend and mythweb report that there are no programs scheduled to be recorded.  If I then kill and restart mythbackend everything is fine and all my scheduled recordings appear.

Why is this happening?  Through phpmyadmin, I've checked every table on numerous occasions but none ever report errors.  I've gone ahead an run repair on all the tables anyway, just to make sure, and that doesn't fix the problem (and I didn't really expect it to).  My mythtv user has full permissions on mythconverg.

Is there something I'm missing?  Would altering the boot order to make sure that mythbackend loads AFTER mySQL make any difference, and if so how do I do that?

For now, I reboot fairly infrequently so this isn't a huge issue, but updates/power outages sometimes demand it and sometimes I'm not around when that happens.  Any help would be greatly appreciated.  Thanks.

---

