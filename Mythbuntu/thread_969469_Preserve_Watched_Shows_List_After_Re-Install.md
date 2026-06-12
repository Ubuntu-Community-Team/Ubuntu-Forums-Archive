---
title: "Preserve Watched Shows List After Re-Install"
date: 2008-11-03
forum: Mythbuntu
---

### Post by Ipsissimus on 2008-11-03
I've been running Mythbuntu 7.10 for the last year with no major hiccups and now want to upgrade to 8.10.  I won't be upgrading because I want to install the new on a fresh set of larger hard disks.

My question is, how do I backup and preserve ONLY the parts of the MythTV database that deal with previously recorded shows.  I will be doing a fresh install and do not want to keep my currently saved shows, so I don't want the entire database backedup.  Which tables in the mythconverg DB keep a list of all previously recorded shows?

Thanks.

---

### Post by novellahub on 2008-11-03
See my post here:

[http://ubuntuforums.org/showpost.php?p=5002555&postcount=3](http://ubuntuforums.org/showpost.php?p=5002555&postcount=3)

The easiest way to do this is run the commands from a flash drive.  Keep in mind you will still need to copy the physical recordings to the new disks.

---

### Post by Ipsissimus on 2008-11-04
Thanks novellahub, I went through the Wiki for mythconverg database scheme and it seems that only the 'oldrecorded' table is used to preserve which shows have already been recorded.  I'm not going to be saving my old recordings on the new install so I guess all I have to backup is:

```
mysqldump -c -u mythtv -p -t mythconverg oldrecorded  > recordings.sql
```

Then just restore that after the new system is up.

-- Thanks.

---

