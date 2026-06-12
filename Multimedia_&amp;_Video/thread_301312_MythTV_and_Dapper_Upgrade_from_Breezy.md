---
title: "MythTV and Dapper Upgrade from Breezy"
date: 2006-11-16
forum: Multimedia &amp; Video
---

### Post by jfinke on 2006-11-16
Here is another MythTV thread...

So, I had a working MythTV setup running for about 7 months.

I was running Breezy and MythTV .19 built from source.

I decided to upgrade to Dapper.  The reason for this was I switched to wireless and went to ethernet.  Unfortunately, the nforce driver (forcedeth) sucks.  It randomly drops my ethernet connection with no errors.  Unfortunately, the upgrade to Dapper did not help even though the driver was updated.  But, that is another story.  ](*,) 

So, I after sorting everything out after the upgrade, things seemed to be working.

However, I started to notice that my scheduler stopped showing upcoming recordings.  So, I obviously started missing some shows.   Everything would come back if I restarted the backend.  

I finally had some tonight to troubleshoot it.  It appears that MySQL 5 and MythTV .19 have some connection issues.  Breezy used 4.0.24.  Dapper upgraded me to 5. So, now that I have that figured out, my question is what to do?

I guess I have several options.

One, would be to downgrade MySQL back to 4.  Is this supported?

Two, I could upgrade MythTV from .19 to .20.  From what I understand this fixes the connection issues.

Three, ????

Any thoughts or ideas?  Thanks!

---

### Post by superm1 on 2006-11-17
I would recommend the jump up to 0.20.  It will resolve your mysql issues, and runs great.

I have repositories with dapper packages built.  

Follow this page to add the repostories.
[https://help.ubuntu.com/community/MythTV/Install/Server/Dapper/Repositories](https://help.ubuntu.com/community/MythTV/Install/Server/Dapper/Repositories)

---

### Post by jfinke on 2006-11-17
Thanks...  I will look into it this weekend.  I will probably just recompile from source again.  Hopefully, it will not be too much work.  :rolleyes:

---

