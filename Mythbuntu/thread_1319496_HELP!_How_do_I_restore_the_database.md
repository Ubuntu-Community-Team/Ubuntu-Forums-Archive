---
title: "HELP! How do I restore the database?"
date: 2009-11-08
forum: Mythbuntu
---

### Post by Captain_Bodge on 2009-11-08
I need to restore my database from the regular backup. (mythconverg.sql.gz)

The script gives instructions on how to remove the database but it also says I need to run the mc.sql script, but doesn't say how to actually do this. That script seems to be just a collection of sql commands, so what is the command line I need to use?

Thanks,

Mark

---

### Post by nickrout on 2009-11-08
> **Captain_Bodge said:**
> I need to restore my database from the regular backup. (mythconverg.sql.gz)

The script gives instructions on how to remove the database but it also says I need to run the mc.sql script, but doesn't say how to actually do this. That script seems to be just a collection of sql commands, so what is the command line I need to use?

Thanks,

Mark

Don't know which script you are using, but the definitive backup script is the one referred to here:

[http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore)

That page also deals with running mc.sql (basically mysql -uroot -p < database/mc.sql , but read the whole page please!)

---

