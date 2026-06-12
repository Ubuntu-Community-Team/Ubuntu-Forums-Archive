---
title: "MythVideo Scan for Changes locks FE"
date: 2012-07-08
forum: Mythbuntu
---

### Post by anonymousdog on 2012-07-08
I must be using Storage Groups wrongly or smthg.  I've avoided Scanning for Changes in MythVideo since upgrading to 0.25 (out of concern for breaking anything), but I've now added a new movie and need to add it to the db.

The problem is that in all FEs including the one on my master BE, "Scan for Changes produces a 0% status bar that never progresses; FE must be killed.  Setup-->Media Settings-->Video Settings-->General Settings has nothing listed in the file path sections so that Storage Groups should apply everywhere.  But, regardless what I have in there (I've tried blank and valid, local paths), the FE searches via myth:// protocol vs local file paths anyway.  BE reveal nothing at all while FE logs show:
```
dirscan.cpp:259 (ScanVideoDirectory) MythVideo::ScanVideoDirectory Scanning Group (myth://Videos@mythtv/var/lib/mythtv/videos/)
``` and nothing else until killed...the MBE is named 'mythtv'.

Existing video files play just fine.

MB 12.04 x86_64/0.25

---

### Post by anonymousdog on 2012-07-12
Running the FE with logging cranked up showed it scanning a handful of(unfortunately deep) directories within the videos storage group directory.  I moved them, and the scans are so quick as to generate no progress bar at all.

---

