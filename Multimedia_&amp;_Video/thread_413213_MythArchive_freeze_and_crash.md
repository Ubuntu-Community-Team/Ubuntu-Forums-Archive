---
title: "MythArchive freeze and crash"
date: 2007-04-18
forum: Multimedia &amp; Video
---

### Post by Dertiger on 2007-04-18
I'm running MythTV .20 on Edgy with no problems.  I installed MythArchive but cannot get it to work.  I can get as far as "Find Files to Archive" or "Export to Media" but when I select either one of those, the machine load will skyrocket (up to ~15) over the next 5 or 10  minutes, after which the kernel kills mythfrontend.  I have tried using different temp folders, verified the USB DVD writer was mapped correctly (/dev/scd0), and even tried with the DVD RW off.  The kernel always kills the process.  What is going on?

As a side note, I noticed as the system load climbs that neither CPU usage nor memory usage is unusual.  What causes the the load numbers to increase even thought the CPU isn't working and memory seems fine (other than out of memory errors from the kernel in /var/log/syslog).

---

### Post by Dertiger on 2007-04-26
I discovered that Edgy did not turn on my swap partition.  After > sudo swapon /dev/hda5 mytharchive ran great.

---

