---
title: "Kino freezes computer on 1394 export"
date: 2010-05-18
forum: Multimedia Software
---

### Post by SixStringSW on 2010-05-18
Actually, I'm having several 1394 issues.

First, the permissions get set to 660 on my raw1394 file every time I log in; Kino seems to expect 777 so I have to change it each time (plus I have to execute /etc/init.d/firewire every time, whatever that does). Otherwise, I get the dreaded "RAW1394 module not found error." Even after doing those steps, I typically have to turn my cam on & off, and leave and re-enter Capture to get Kino to get past the "AV/C compliant" message and actually see and utilize my camcorder.

My main problem, though, is every time I try to Export 1394 back to my cam, the computer freezes solid, requiring h/w power cycle. If I Resample Audio, it freezes with the "Locking audio (0%)" status message; if I don't, it freezes immediately. If I try Preview, Kino itself locks up, but I still have mouse movement. However, if I Force Quit on Kino, I get another hard freeze.

I can export to DV File, no problem, so it seems to be a 1394 issue. I wonder if it's related to the raw1394 issues mentioned above.

Any ideas? I'm running Kino 1.3.4 (that I compiled) under Jaunty.

Thanks.

---

