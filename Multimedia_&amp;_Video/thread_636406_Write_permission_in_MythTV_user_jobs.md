---
title: "Write permission in MythTV user jobs"
date: 2007-12-09
forum: Multimedia &amp; Video
---

### Post by Bofirial on 2007-12-09
I use a script to convert a files format using ffmpeg and save it on my NTFS partition.  When I run the script everything works fine.  However when MythTV runs it as a user job it fails with a "could not open" error.

So the job just doesn't have write permission.  I've been able to fix this with umask=(0,0,0) on my NTFS partition but I was curious if there was a safer solution.

Thanks for your help.

Script: [http://www.mythtv.org/wiki/index.php/Ipod_export](http://www.mythtv.org/wiki/index.php/Ipod_export)

---

### Post by Bofirial on 2007-12-10
One bump before I just go back to the old way of doing it.

---

