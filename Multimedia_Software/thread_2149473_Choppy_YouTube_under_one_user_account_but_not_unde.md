---
title: "Choppy YouTube under one user account but not under another"
date: 2013-05-28
forum: Multimedia Software
---

### Post by bobprobst on 2013-05-28
Ubuntu 12.04 LTS and Chrome [COLOR=#303942][FONT=Ubuntu]Version 27.0.1453.93

I can playback video just fine under my ubuntu account but when my son logs into his own profile Youtube is extremely choppy.

I tried a suggestion to run gstreamer-properties and set output to X Windows System (No Xv).  That did not help.

The videos buffer just fine but they just jerk from one frame to the next. And if I watch the elapsed time on the video, it skips as well.

Sound playback is fine and smooth.

Thanks for any suggestions

SOLVED

Kept tinkering and comparing my install to my son's.  He had flash [/FONT][/COLOR]11.7.700.203 installed and I had 11.2 r202.  I uninstalled 11.7 and installed 11.2.  Badabing Badaboom.

Everything is fine now.

/obvious

---

