---
title: "[SOLVED] Frontend looses backend connection daily"
date: 2008-10-22
forum: Mythbuntu
---

### Post by iitywygms on 2008-10-22
I am fairly new to mythbuntu.  I have had it up and running pretty solid the last few weeks but yesterday and today when I got home, i tried to watch tv and it said it cannot connect to backend server.  Yesterday I just reebooted the computer and that fixed it so I just chalked it up as a glitch.  Today the same thing happended and when I restarted it said it could not find upnp server.  I had to restart 4  times before I could get it working again.  It also asked me what language to use and had me setup a few things before the frontend would work.
Please let me know what information I can provide and what steps I should take.  I really got nervous today..

In the /var/log/mythtv/frontend.log file I saw this (NVP: Prebuffer wait timed out 10 times) at least a gazillion times.
I also noticed that it did not run the commercial flagger last night on any recordings.


specs:
combined front and back end on one computer.
8.04
nvidia

---

### Post by iitywygms on 2008-10-23
Fixed.  Had file system errors.  FSCK fixed it right up.

---

