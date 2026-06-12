---
title: "Mythtv, Mysql restore from old box"
date: 2007-03-14
forum: Multimedia &amp; Video
---

### Post by ebike on 2007-03-14
Hi All,

I am wanting to "upgrade" my Gentoo based Mythtv box to an Ubuntu based one.

My only concern is migrating the Mysql database to the new system. Can anyone outline the 
steps to backup my existing database, and how to insert it into the relevent procedure outlined in the "Mythtv/Edgy Backend Frontend" howto.

Thanks.

---

### Post by cyberdork33 on 2007-03-14
use phpmyadmin

---

### Post by markitect on 2007-03-14
```
back it up:
 mysqldump databasename > backupfile

restore it:
mysqlimport databasename backupfil

```

---

### Post by majoridiot on 2007-03-14
this is the method i have used successfully- i.e. zero errors... i've moved my database/backend appx
6 times in the past 3 mos...

on the backend with the database you want to backup:

```
# mysqldump -u mythtv -pmythtv mythconverg -c > mythtv_backup.sql
```

the -p argument is the password to the mythconverg database.  check yours to be sure what yours is.
it's in the hidden folder .mythtv in your mythtv home directory in the file mysql.txt:

```
# gedit ~/.mythtv/mysql.txt
```

line 3, DBPassword=xxx  where xxx is your password.  if yours is different than the one above, substitute
yours behind the -p argument- *no spaces between*.  e.g. -pyourpassword.

make a copy of the mythtv_backup.sql file (it can be quite large).

If the only thing you are changing is moving from gentoo to ubuntu (congrats!), then On the new 
install, work through the guide up to the ***InitialConfiguration*** page of the ***mythtv-setup step***

Complete the first two config pages of ***mythtv-setup***- ***Host Address Backend setup*** and
***Host Specific Backend Setup***.  when you have those two pages filled in with your info, you can
exit from mythtv-setup (ignore any warnings it may give) and then restore your DB:

```
# mysql -u root
```

if your mysql has a *root password*, (it won't unless you set it installing) instead do:

```
# mysql -u root -p
```

and then enter your *root mysql* password.  when the mysql prompt comes up, do:

```
mysql> DROP DATABASE mythconverg;
mysql> create database mythconverg;
mysql> exit
```

check to see if the new installation of mythtv has changed the mysql password by checking mysql.txt
as described above, and then restore the database, substituting the new mythtv DB password if necessary:

```
# mysql -u mythtv -p mythconverg < mythtv_backup.sql
```

once you do that, you can return to ***step 6 of  Install MythTV***:

[https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop#head-21357a0059b3986ca1052c0a987386f54cd5e338](https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop#head-21357a0059b3986ca1052c0a987386f54cd5e338)

if you want, you can do step 6 to fill the guide with data (not necessary if your restored DB was current)... or just continue at step 7.

good luck!

---

### Post by ebike on 2007-03-14
Wow! Great help, I will try that tonight, thanks majoridiot   :) 

Cheers.

---

### Post by majoridiot on 2007-03-16
you're welcome.  hope it works out for you!

---

