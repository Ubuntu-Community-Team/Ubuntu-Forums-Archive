---
title: "Dvico Dual Digital 4 suddenly stopped working"
date: 2008-01-30
forum: Multimedia &amp; Video
---

### Post by MrHyde on 2008-01-30
Hi,

I hope someone can help me with this problem.  I have a Dvico Dual Digital 4 card that has been working with MythTV and Ubuntu Gutsy Gibbon 7.1 with no problems for over 6 months.  Today, while changing channels, my computer suddenly froze.  Shutting down the frontend did not bring it back up.  So, I restarted the server.

Everything came up except the TV Tuner cards.  My mythtv setup shows the two video capture cards, but when I go into their configuration, the frontend ID says "Could not open card #0 Subtype: No such file or directory".  When working, it would say "Zarlink ZL10353 DVB-T Subtype: DVB-T"

Running lsusb shows 
Bus 009 Device 003: ID 0fe9:db78 DVICO
Bus 009 Device 002: ID 0fe9:db78 DVICO

I don't know what else to check.  Can someone please provide suggestions on what else I can check or do.  I don't know much about Linux and hardware drivers and such, so don't even know how to tell that the card drivers are loaded and working properly.  I don't understand what could have been corrupted by a restart.  I have restarted the server numerous times with no problems.

Thank you.

MrHyde

---

### Post by RawMustard on 2008-01-30
Did you install the drivers yourself?  Maybe they're corrupt and need reinstalling.
It could also be that your card has died causing the lockup.

---

### Post by nasha on 2008-03-06
I had similar problems with my Dual Digital 4 a couple of times believe it or not!
To solve the problem, i recompiled the latest v4l-dvb drivers and installed them, as well as deleting the firmware, and wget them again. Then delete the tuners in mythtv-setup and then recreate them, attach them to your source, and everything would be fine again :)
Out of curiosity, do you have your remote working? (I currently have IR problems)

Hope this helps :)
Nasha

---

