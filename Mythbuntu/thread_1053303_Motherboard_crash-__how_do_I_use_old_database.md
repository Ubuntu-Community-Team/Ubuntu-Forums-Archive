---
title: "Motherboard crash-  how do I use old database?"
date: 2009-01-28
forum: Mythbuntu
---

### Post by itlarson on 2009-01-28
Due to a motherboard failure I am installing a new processor and motherboard in my myth box.  If I have to reinstall the os,  how do I reuse the data from my old install?

---

### Post by klc5555 on 2009-01-29
> **itlarson said:**
> Due to a motherboard failure I am installing a new processor and motherboard in my myth box.  If I have to reinstall the os,  how do I reuse the data from my old install?

If you've got a copy of the mythconverg.sql database file that's in good shape, you're OK. It has all your tuner hardware settings, all your channel, guide, and program information, and all your recordings information. If you have not done database backups, try to boot something without reinstalling Mythbuntu until you can secure a copy of this file. In addition, depending on your version of Mythbuntu (I think) there should have been a once-weekly automated backup of the mythconverg database that is in the mythtv users directory. If you do a lot of recording it will be a bit out of date, but recordings from a date later than the backup can be readded eventually with the myth.rebuilddatabase.pl script.

If you have secured a good copy of the database, either compressed (.gz, .bz2) or uncompressed, you can reinstall the OS without losing anything but time, so long as your recordings drives (or partitions) are left unmolested by the reinstallation. After OS reinstallation, a stub mythconverg can be created and your database backup restored into it using the information found in the myth manual here: [http://www.mythtv.org/wiki/User_Manual:Periodic_Maintenance](http://www.mythtv.org/wiki/User_Manual:Periodic_Maintenance) 

After the restore, you will likely have to go into the backend setup, delete and readd all your tuners, and maybe rescan, because your hardware profile will have changed with the new mobo. But everything else should be unaffected.

Make sure you set up a (daily!) database backup script like the models shown on the manual page cited above. Make sure it copies the backup to somewhere outside your machine's root partition. (A copy to wherever your recordings are kept is not a bad idea.) One very bad hardware weekend for me 8 months ago had 6 complete OS reinstallations. But I didn't lose any recordings or data! Just sleep. :D

Good luck! :)

---

### Post by itlarson on 2009-02-01
belated thanks- I'll make a copy of mythconverge.mysql before proceding with the install.

---

