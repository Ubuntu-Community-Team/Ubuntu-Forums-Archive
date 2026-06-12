---
title: "Is there something like a channel list in Mythtv?"
date: 2010-06-20
forum: Mythbuntu
---

### Post by seppl82 on 2010-06-20
Hi,

i've grabbed trough some wiki entries but don't find an answer for the latest Version of mythtv.
Is there something like a channel list that i can backup or modify?

Kind Regards
/Seppl

---

### Post by ian dobson on 2010-06-20
Hi,

If you have mythweb intalled you can play wth the channels in the setting screen.

The actual channel list is in the mysql database, along with almost everything else.

Regards
Ian Dobson

---

### Post by seppl82 on 2010-06-20
Hi,

thanks a lot. I wan't to reinstall my system. What can i do to preserve the list?

Kind Regards
/Seppl

---

### Post by ian dobson on 2010-06-20
Hi,

This command will dump the entire sql database to a compressed file in the current directory.

mysqldump -uUSER -pPASSWORD --all-databases --opt | bzip2 > backup-sql.bz2

Regards
Ian Dobson

or maybe google for mysql backup/restore,you might find a better way.

---

### Post by seppl82 on 2010-06-20
And how can i reimport the Database?

---

### Post by uncle hammy on 2010-06-20
[http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore)

---

### Post by nickrout on 2010-06-20
For heaven's sake use the method referred to in the wiki to back up your database, ie the one pointed to by uncle hammy!

---

### Post by seppl82 on 2010-06-21
Okay, thanks for you're contribution.
I'll try Toad for mysql :-)

---

