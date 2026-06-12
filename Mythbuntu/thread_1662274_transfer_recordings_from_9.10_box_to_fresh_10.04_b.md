---
title: "transfer recordings from 9.10 box to fresh 10.04 build"
date: 2011-01-07
forum: Mythbuntu
---

### Post by frego on 2011-01-07
I've built a new backend/frontend Mythbuntu 10.04 machine to replace my 9.10 Mythbuntu box.  I'd like to preserve my recordings if I could.  I see they are in /var/lib/mythtv/recordings.  So I'm sure I can easily copy and paste and fix any permissions/ownership issues.  But how do I get the metatag info into the database?  I googled around some and found one random website that recommended:

> $ mysqldump -u mythtv -pmythtv mythconverg -c > mythtv_backup.sql
$ grep "INSERT INTO \`record\` "          mythtv_backup.sql > restore.sql
$ grep "INSERT INTO \`recorded\` "        mythtv_backup.sql >> restore.sql
$ grep "INSERT INTO \`oldrecorded\` "     mythtv_backup.sql >> restore.sql
$ grep "INSERT INTO \`recordedprogram\` " mythtv_backup.sql >> restore.sql
$ grep "INSERT INTO \`recordedrating\` "  mythtv_backup.sql >> restore.sql
$ grep "INSERT INTO \`recordedmarkup\` "  mythtv_backup.sql >> restore.sql
$ grep "INSERT INTO \`recordedseek\` "    mythtv_backup.sql >> restore.sql
$ mysql -u mythtv -pmythtv mythconverg <>

Is this the preferred way of doing this or is there a better way to transfer recordings?

---

### Post by IceCap on 2011-01-07
Search for scripts called "mythconverg_backup.pl" and "mythconverg_restore.pl" and directions on how to use them.  You need to use those to make a backup of your mysql database and the restore it in the new system.

  I did this while back when upgrading from 8.10 to 9.04 and it worked amazingly well (can I say that?).

  Also, I'm sure you will get more detailed explanation on how to do this.

  IC

---

### Post by newlinux on 2011-01-08
[http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore)

Should give you a good start. Let us know if you have more questions

---

### Post by frego on 2011-01-08
mythconverg_restore.pl looks like it will drop my existing database and overwrite with the settings from the old.  I have some recordings on the new box and my configuration that I would like to keep.  Can anyone advise on how best to proceed?

---

### Post by nickrout on 2011-01-08
suggest you ask on the mailing list, there are plenty of database gurus there?

---

### Post by newlinux on 2011-01-08
The mailing list, as nickrout said, is where to go for help, but with any advice (if any) anyone gives you on how to do what you want (a partial merge, effectively) be sure to take a backup of your existing production database, as this is likely to get a little murky.

---

