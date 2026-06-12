---
title: "Mythtv won't run User Jobs"
date: 2009-11-16
forum: Multimedia Software
---

### Post by scott_g on 2009-11-16
Hi,

I'm trying to get mythtv to export my TV shows to xvid files (to save space), but I can't seem to get it to run a command from the user job.  To make the command as simple as possible, I've been using the following command:

```

sudo -u scott echo "%TITLE%" > /home/scott/log.txt

```

But, the file log.txt is never affected.  The backend log says this:
```

2009-11-16 23:23:52.323 JobQueue: Started "Xvid Conversion" for "The Big Bang Theory" recorded from channel 1005 at Mon Nov 16 21:31:00 2009
[sudo] password for mythtv: 
2009-11-16 23:23:54.541 JobQueue: Finished "Xvid Conversion" for "The Big Bang Theory" recorded from channel 1005 at Mon Nov 16 21:31:00 2009.

```

Does anyone have any ideas?

Thanks,
Scott

---

