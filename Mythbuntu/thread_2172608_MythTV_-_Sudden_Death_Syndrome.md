---
title: "MythTV - Sudden Death Syndrome"
date: 2013-09-05
forum: Mythbuntu
---

### Post by mark55 on 2013-09-05
One day my Mythbuntu (12.04 with MythTV 0.25 I believe) was running perfectly, the next day it wasn't.

This is a combined Frontend/Backend system on a single box.  It is a pure system, I haven't added anything.

My first clue was when the web interface stopped responding.

On switching on the attached monitor I was confronted by the Frontend language confirmation screen.  This despite the fact that I hadn't restarted anything since the previous day.  An autonomous reboot perhaps?

On clicking through the language screen, it presented a message to the effect of "unable to connect to database".

I clicked through these screens, with the default values as offered as I never set anything special here originally.  After clicking finished, the screen immediately returned to language selection.

A bit of Binging, led me to a post about increasing the retry time and number of retries.  This didn't solve the problem, but it did at least introduce a delay into the return of the language screen so I could see the desktop.

I disabled the Frontend Autostart feature, and rebooted.

On the reboot, the Myth logo flashed past briefly, followed by a few lines of console text, ending at:

apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for server name  [OK]
*starting web server apache2 [OK]

after which nothing else happens.  This is consistent across multiple reboots.

I've been back through a year or more of the MythTV list archives, and a couple of years of this forum, and found no similar reports.

So, any suggestions for recovery and/or further debug?  Though it seems so badly stuffed that reinstallation appears likely.

What can I usefully recover for reuse if I have to reinstall?

Courtesy of a Puppy Live CD, I have been able to recover my recordings to external storage.

Your suggestions are welcomed.

Thanks.

---

### Post by tgm4883 on 2013-09-05
> **mark55 said:**
> One day my Mythbuntu (12.04 with MythTV 0.25 I believe) was running perfectly, the next day it wasn't.

This is a combined Frontend/Backend system on a single box.  It is a pure system, I haven't added anything.

My first clue was when the web interface stopped responding.

On switching on the attached monitor I was confronted by the Frontend language confirmation screen.  This despite the fact that I hadn't restarted anything since the previous day.  An autonomous reboot perhaps?

On clicking through the language screen, it presented a message to the effect of "unable to connect to database".

I clicked through these screens, with the default values as offered as I never set anything special here originally.  After clicking finished, the screen immediately returned to language selection.

A bit of Binging, led me to a post about increasing the retry time and number of retries.  This didn't solve the problem, but it did at least introduce a delay into the return of the language screen so I could see the desktop.

I disabled the Frontend Autostart feature, and rebooted.

On the reboot, the Myth logo flashed past briefly, followed by a few lines of console text, ending at:

apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for server name  [OK]
*starting web server apache2 [OK]

after which nothing else happens.  This is consistent across multiple reboots.

I've been back through a year or more of the MythTV list archives, and a couple of years of this forum, and found no similar reports.

So, any suggestions for recovery and/or further debug?  Though it seems so badly stuffed that reinstallation appears likely.

What can I usefully recover for reuse if I have to reinstall?

Courtesy of a Puppy Live CD, I have been able to recover my recordings to external storage.

Your suggestions are welcomed.

Thanks.

Strange. Sounds like you might have a bad drive.

---

