---
title: "Missing Recordings"
date: 2011-10-05
forum: Mythbuntu
---

### Post by remarkosmoc on 2011-10-05
Hello,

I have a few recordings that have gone missing.  The frontend reports that "Recording Unavailable  <show info> The file for this recording can not be found"

When I look in the recorded table I see what file it is looking for, I can find it and play it with vlc fine so I know the file is there and working.  

The other item of interest is the filesize field in the recorded table for the recording is 0 

I had this happen to about 3 recordings now (that I know of I'm a bit behind on my TV)

Thanks,

Remark

---

### Post by nickrout on 2011-10-06
> **remarkosmoc said:**
> Hello,

I have a few recordings that have gone missing.  The frontend reports that "Recording Unavailable  <show info> The file for this recording can not be found"

When I look in the recorded table I see what file it is looking for, I can find it and play it with vlc fine so I know the file is there and working.  

The other item of interest is the filesize field in the recorded table for the recording is 0 

I had this happen to about 3 recordings now (that I know of I'm a bit behind on my TV)

Thanks,

Remark

perhaps your database is damaged, or a storage group is not mounted.

run /etc/cron.weekly/mythtv-database and see if it reports errors.

---

