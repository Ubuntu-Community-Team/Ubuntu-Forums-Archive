---
title: "Recorded programs gone except in MythWeb"
date: 2009-12-06
forum: Mythbuntu
---

### Post by NightStorm on 2009-12-06
*** Never Mind: solved

It was self-inflicted (there is nothing like asking for help to realize the solution).
I discovered that the Watch-Recordings has a group filter and that it somehow got set to a single series.

Thanks for reading.

***


Original message:

After rebuilding, I'm having an odd issue where MythWeb shows my recorded programs but the front end only shows 3 (out of approx. 100) of them.

I needed to reorganize my storage (new HD) on an existing Mythbuntu 9.10 system so I did this:
  Followed the directions at:
   [http://www.mythpvr.com/mythtv/tips/migrate-recordings.html](http://www.mythpvr.com/mythtv/tips/migrate-recordings.html)

to create a "recordings.sql" file and saved it.
Made a backup of my /var/lib/mythtv/recordings directory

Did a from-scratch install to create a new system on the same hardware but now having two drives mounted under /myth1 and /myth2
Created the directories "recordings", "livetv", and "videos" under these two directories.  Matched their permissions and ownerships to those under /var/lib/mythtv.

Copied all of the old /var/lib/mythtv/recordings/* to /myth1/recordings.

In mythtv-setup I changed the storage directories for "Default" to be /myth1/recordings/ and /myth2/recordings

I imported the old recordings.sql as per the web page cited earlier.

Once I did that everything showed up under mythweb and the old recordings can be played via the web interface.  However mythfrontend -> Media Library-> Watch Recordings shows only three entries (three different episodes of the same show title) and no more.

I've tried looking through the various myconverg tables (in particular the "recorded", "recordedfile" and "recordedprogram" tables but am at a loss.

I would greatly appreciate any suggestions on how to diagnose this.

---

### Post by trubblemaker on 2010-01-15
Thanks for this post.  My wife accidentally did this to me and without this post I would have gone craZY

---

