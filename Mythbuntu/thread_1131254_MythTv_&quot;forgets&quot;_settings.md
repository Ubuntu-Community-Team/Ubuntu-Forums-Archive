---
title: "MythTv &quot;forgets&quot; settings"
date: 2009-04-20
forum: Mythbuntu
---

### Post by dotnick on 2009-04-20
I have just added a second frontend to my backend/frontend setup.  And the box in mythbuntu-control-centre that controls the mysql server reverts to the disabled state after a reboot.  If I change it back, everything is hunky dory until it reboots.

And, for the remote frontend, I've been trying to add a /usr/bin/wakeonlan MACADDRESS command to the server wakeup field in mythfrontend setup.  But no matter what, once the menu is closed, the changes I made disappear.

And to further confuse matters, for the first time ever has MythTv loaded my files library so that I can watch recordings and livetv, but did not load my scheduled recordings.  I have to restart my backend for the recording schedules to come back.

If theres a common denominator, I have no idea what it is.

I am using Jaunty Beta right now and the VDPAU builds.

---

### Post by dotnick on 2009-04-20
I've just noticed that while rebooting, and looking for upcoming recordings, that through MythWeb the recordings searches seem to exist, yet no upcoming recordings are shown as scheduled (until mythbackend is restarted) ... maybe this one is a bug in my build?

also, the mysql box stayed checked this time.... maybe not a problem after all

---

### Post by dotnick on 2009-04-21
I believe I've found the bug report for the recording schedule not showing up.  This must be a common problem in the recent Jaunty builds.

[https://bugs.launchpad.net/ubuntu/+source/mysql-dfsg-5.0/+bug/326768](https://bugs.launchpad.net/ubuntu/+source/mysql-dfsg-5.0/+bug/326768)

As far as the second frontend goes, I've noticed that it brings all of it's settings in from the database, which is on the backend, which is not ideally on when the second frontend is started.  (defeats my purpose)  ... I have found posts that the mythbuntu diskless server, with the write to usb pen drive option, may solve those problems too.

---

