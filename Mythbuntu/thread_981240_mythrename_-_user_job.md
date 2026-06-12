---
title: "mythrename - user job"
date: 2008-11-13
forum: Mythbuntu
---

### Post by verevi on 2008-11-13
Hi,

I setup mythrename to run after a recording.  It runs, but fails.  It works fine if I do it from the command line, but the mythbackendlog shows the following error:

```
2008-11-13 11:30:45.386 JobQueue: Started "mythrename" for "Judge Alex" recorded from channel 1071 at Thu Nov 13 11:24:00 2008
No config found; attempting to find mythbackend via UPnP.
No backends found.  Please copy /home/mythtv/.mythtv/config.xml from a working MythTV installation instead.
Compilation failed in require at /usr/share/doc/mythtv-backend/contrib/mythrename.pl line 22.
BEGIN failed--compilation aborted at /usr/share/doc/mythtv-backend/contrib/mythrename.pl line 22.
```

Some environmental setting not being loaded?  How do I get it to run?

Thanks for any suggestions.

---

### Post by anonymousdog on 2008-11-13
I find no ./.mythtv/config.xml in the home directory of my mythbackend user.  In my case, it's mythtv, so, /home/mythtv/.mythtv/config.xml (does not exist).  The script must use this file for db settings.  Copy the one in your mythfrontend home directory (to the path above) and set file ownership to your backend service account and group.

---

### Post by verevi on 2008-11-13
That worked.  Thanks a bunch.

---

