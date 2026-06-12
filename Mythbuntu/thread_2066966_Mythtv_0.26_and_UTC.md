---
title: "Mythtv 0.26 and UTC"
date: 2012-10-05
forum: Mythbuntu
---

### Post by GuiGuy on 2012-10-05
The wiki states
> The conversion to UTC requires significant changes to the database, and may be problematic for some users. MythTV will automatically attempt to perform a database backup before any schema update, storing the dump to the current user's home directory, or any storage path MythTV has been informed of, so that if anything goes wrong in the process, the database can be rolled back to the previous functional state. If MythTV cannot find anywhere with write access to store the backup, it will proceed with the update anyway, so users may want to perform their own periodic backups just to be safe. Refer to Database_Backup_and_Restore#Quick_Start for more information. 

I was wondering, might the change upset the scripts I use that automatically put my mythbuntu backend to sleep and wake it as required? 

Thanks

---

### Post by nickrout on 2012-10-05
> **GuiGuy said:**
> The wiki states


I was wondering, might the change upset the scripts I use that automatically put my mythbuntu backend to sleep and wake it as required? 

ThanksProbably more a dev question, you may get a better response on the mailing list.

---

### Post by GuiGuy on 2012-10-05
> **nickrout said:**
> Probably more a dev question, you may get a better response on the mailing list.

Thanks. I killed my subscription a while back; too much information :)

But you're probably right.

Cheers

---

### Post by BicyclerBoy on 2012-10-06
Couple months ago (?) I added the UTC timezone stuff into mysql.
At that moment was still using mythtv0.25+fixes on lucid..

Caused no problems with recordings or auto shutdown/RTC-alarm wakeup.. 

Some aussie users revealed a couple of weird bugs due to their timezone offset..

---

### Post by GuiGuy on 2012-10-06
> **BicyclerBoy said:**
> Couple months ago (?) I added the UTC timezone stuff into mysql.
At that moment was still using mythtv0.25+fixes on lucid..

Caused no problems with recordings or auto shutdown/RTC-alarm wakeup.. 

Some aussie users revealed a couple of weird bugs due to their timezone offset..

Thanks. I'm going to image the installation onto a spare HDD and then to the move. Just in case...;)

Cheers

---

### Post by BicyclerBoy on 2012-10-07
There are 2 parts to this 0.26 UTC & I don't see any need to change 2 different components at the same time.

The UTC timezone tables are required to be added to mysql.
These TZ tables/installer are not new & afaik have been available as option for years (for mysql).

It is the mythtv schema mythconverg that is irreversibly changed (as usual) by myth upgrades.

---

### Post by nickrout on 2012-10-07
> **BicyclerBoy said:**
> There are 2 parts to this 0.26 UTC & I don't see any need to change 2 different components at the same time.

The UTC timezone tables are required to be added to mysql.
These TZ tables/installer are not new & afaik have been available as option for years (for mysql).

It is the mythtv schema mythconverg that is irreversibly changed (as usual) by myth upgrades.

That's right adding the TZ tables to mysql will not do anything to an 0.25 system. The tables only tell mysql about the differences between timezones.

When you upgrade to 0.26 nysql will use thse TZ tables to alter all the times in your database to UTC intead of localtime. That is the danger point, if something goes wrong.

---

