---
title: "Dealing with vino flakiness"
date: 2013-02-04
forum: Networking &amp; Wireless
---

### Post by geofgibson on 2013-02-04
I understand from searching around that vino being flaky and not responding while it is in fact running is not unusual.  I'm trying to find a solution and wanted to put this out there to see if I'm crazy or just wrong.
If I were to create a cron job which restarted vino-server every night, that seems to me it might solve the problem because, when I am at the machine and I can't get vino to respond, all I usually do is bring up the screen sharing control panel and click screen sharing off and back on and then vino responds.  Seems logical, yes?

What I am not sure how to approach is writing the script.  I'm guessing I'd need to kill the instance of vino-server?  Here's where I'm fuzzy.  Do a grep on ps -a to find vino's pid and use that as the variable for the kill command?  Once that's done then just execute vino-server again?

Any assistance would be most appreciated, thanks.

---

