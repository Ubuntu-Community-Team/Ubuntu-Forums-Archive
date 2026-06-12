---
title: "Mythtv 'Import DVD' issue"
date: 2007-12-09
forum: Multimedia &amp; Video
---

### Post by trieb on 2007-12-09
I could not figure out why I could play a DVD from the DVD menu in mythtv, but not import one.  It turns out that for the install on Gutsy, the setup parm which specifies the cd device to be used only applies to the playback tool.  The import function, calling transcode, looked for /dev/dvd regardless of what you specified in the settings menu.  Realizing that I only had dvd1 listed in /dev/, creating the link dvd->scd0 fixed the problem.

---

