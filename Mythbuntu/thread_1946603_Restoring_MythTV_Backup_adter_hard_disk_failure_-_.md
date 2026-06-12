---
title: "Restoring MythTV Backup adter hard disk failure - password problem!"
date: 2012-03-25
forum: Mythbuntu
---

### Post by markofealing on 2012-03-25
My mythbuntu PC is configured as a combined front end/ backend using a 1Tb Data drive and a 80Gb boot drive.

All backups are stored on the Data drive on the basis that should the boot drive fail, I can restore the database from the backups. Nice theory and it has worked well in the past when the database has got currupted.

Unfortunately, the boot drive died last week so I've been rebuilding the PC using a replacment disk. All has been well until I've got round to restoring the database using:

mysql -u mythtv -p   mythconverg < *mythtvbackup_filename*.sql

The restore requests a password, which I would normally obtaine from .mythtv/mysql.txt, except that file is in on the boot drive which is for all intents and purposes dead! Head failure.

The new mythtv install uses a diffent password, so this will not work. This seems to leave me with an unusable backup to restore from!

In hindsight I should have copied the mysql.txt file to the DB_backups directory on the Data drive to aviod this problem or change the mysql password. Such is the power of hindsight.

**Other than starting with a new database, does anyone have any suggestions on how to resolve this problem?**

---

### Post by tgm4883 on 2012-03-25
> **markofealing said:**
> My mythbuntu PC is configured as a combined front end/ backend using a 1Tb Data drive and a 80Gb boot drive.

All backups are stored on the Data drive on the basis that should the boot drive fail, I can restore the database from the backups. Nice theory and it has worked well in the past when the database has got currupted.

Unfortunately, the boot drive died last week so I've been rebuilding the PC using a replacment disk. All has been well until I've got round to restoring the database using:

mysql -u mythtv -p   mythconverg < *mythtvbackup_filename*.sql

The restore requests a password, which I would normally obtaine from .mythtv/mysql.txt, except that file is in on the boot drive which is for all intents and purposes dead! Head failure.

The new mythtv install uses a diffent password, so this will not work. This seems to leave me with an unusable backup to restore from!

In hindsight I should have copied the mysql.txt file to the DB_backups directory on the Data drive to aviod this problem or change the mysql password. Such is the power of hindsight.

**Other than starting with a new database, does anyone have any suggestions on how to resolve this problem?**

The -p options is why it is asking you for a password. It's not asking you for your old password though, it's asking you for your new password (in your new database). You might try restoring the DB using the mysql root user (and mysql root password).

Also, next time use one of the available utilities to backup your database. The MythTV team has a database backup and restore perl script.

---

### Post by klc5555 on 2012-03-25
> **tgm4883 said:**
> The -p options is why it is asking you for a password. It's not asking you for your old password though, it's asking you for your new password (in your new database). You might try restoring the DB using the mysql root user (and mysql root password).


The original poster didn't realize his backup with mysqldump backed up only data and is not password protected. Therefore the new mysql.txt password from the new installation is all that's needed here for him to complete his planned restore with user "mythtv". The root user won't be necessary. The old database's data will load perfectly into his new, essentially empty mythconverg.

---

### Post by markofealing on 2012-03-26
Many thanks to both KLC5555 and TGM4883, the database restored okay using the mysql.txt password from the new install.

I think where I was going wrong was trying to copy and paste in the password rather than typing it in.

---

### Post by nickrout on 2012-03-26
In future you might like to consider using the proper backup and restore utility provided by the mythtv developers. There is a long article about it in the wiki.

---

