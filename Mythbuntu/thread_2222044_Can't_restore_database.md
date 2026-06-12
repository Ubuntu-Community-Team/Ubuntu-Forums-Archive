---
title: "Can't restore database"
date: 2014-05-04
forum: Mythbuntu
---

### Post by itlarson2 on 2014-05-04
I have installed 14.04, but can't get the database to restore.  I kep getting error mesages like this:

~/backup$ /bin/sh mythconverg_restore.pl --drop_database --create_database --directory /home/jsl-sll/backup --filename mythconverg-1299-20140504020002.sql.gz
mythconverg_restore.pl: 11: mythconverg_restore.pl: use: not found
mythconverg_restore.pl: 12: mythconverg_restore.pl: use: not found
mythconverg_restore.pl: 15: mythconverg_restore.pl: =: not found
mythconverg_restore.pl: 16: mythconverg_restore.pl: =: not found
mythconverg_restore.pl: 19: mythconverg_restore.pl: Syntax error: word unexpected (expecting ")")

I tried deleting the database:

mysql -uroot -p -e 'DROP DATABASE IF EXISTS mythconverg;'

and recreating it:

mysql -uroot -p -e 'CREATE DATABASE IF NOT EXISTS mythconverg;'

but now the backend seems to be crashing as soon as it starts:

$ sudo service mythtv-backend status
mythtv-backend stop/waiting
$ sudo service mythtv-backend start
mythtv-backend start/running, process 2740
$ sudo service mythtv-backend status
mythtv-backend stop/waiting

---

### Post by blm-ubunet on 2014-05-04
Stop trying to run the mythconverg script as a shell script...it is perl  So just use (in same folder as script) : 

```
./mythconverg_restore.pl --drop_database --create_database --directory /home/jsl-sll/backup --filename mythconverg-1299-20140504020002.sql.gz
```

If that fails check you have the mythtv-perl (& python) bindings installed.

You should always run mythtv-setup (NOT as root) after any update/install.
Make sure backend is stopped with
```
sudo service mythtv-backend stop
```

---

### Post by aelfric55 on 2014-05-05
> **itlarson2 said:**
> I have installed 14.04, but can't get the database to restore.  I kep getting error mesages like this:

~/backup$ /bin/sh mythconverg_restore.pl --drop_database --create_database --directory /home/jsl-sll/backup --filename mythconverg-1299-20140504020002.sql.gz
mythconverg_restore.pl: 11: mythconverg_restore.pl: use: not found
mythconverg_restore.pl: 12: mythconverg_restore.pl: use: not found
mythconverg_restore.pl: 15: mythconverg_restore.pl: =: not found
mythconverg_restore.pl: 16: mythconverg_restore.pl: =: not found
mythconverg_restore.pl: 19: mythconverg_restore.pl: Syntax error: word unexpected (expecting ")")

I tried deleting the database:

mysql -uroot -p -e 'DROP DATABASE IF EXISTS mythconverg;'

and recreating it:

mysql -uroot -p -e 'CREATE DATABASE IF NOT EXISTS mythconverg;'

but now the backend seems to be crashing as soon as it starts:

$ sudo service mythtv-backend status
mythtv-backend stop/waiting
$ sudo service mythtv-backend start
mythtv-backend start/running, process 2740
$ sudo service mythtv-backend status
mythtv-backend stop/waiting

You have made yourself a new, stubby, no-information mythconverg. Your preferred backup is just a zipped mysqldump file. Put a copy of this backup file in your user home directory, unzip  it manually, and then try restoring it the old-fashioned way:```
$ mysql -u mythtv -p   mythconverg < mythconverg-1299-20140504020002.sql
```Supply the mysql password and let it chug away for the 2-15 minutes it takes. Restart mysqld. Your backend should be able to run. Probably needs to be started manually the first time.

Then figure out what's wrong with your perl bindings.

---

### Post by dannyboy79 on 2014-05-05
you can't just create a mythconverg database like that i don't think. did you use mc.sql file?

---

### Post by aelfric55 on 2014-05-06
> **dannyboy79 said:**
> you can't just create a mythconverg database like that i don't think. did you use mc.sql file?

Sure you can. It's simple to log into mysql, and at the mysql prompt```
mysql> **CREATE DATABASE mythconverg;**
```which produces a mythconverg stub with 1 table and 1 entry. A full mysqldump database backup can then be restored onto this stub. The only time I've ever needed to use the mc.sql file was when the jump from mysql 5.1 to mysql 5.5 took place a few years ago, causing a fair amount of breakage.

---

### Post by itlarson2 on 2014-05-06
I have clearly created a non functional database, which is probably why the backend is crashing.  I will try the following tonight:

mysql -uroot -p -e 'CREATE DATABASE IF NOT EXISTS mythconverg;'
mysql -uroot -p -e 'DROP DATABASE IF EXISTS mythconverg;'
 mysql -u mythtv -p   mythconverg < mythconverg-1299-20140504020002.sql

Hopefully this will bypass the backup script which doesn't seem to be working.

---

### Post by blm-ubunet on 2014-05-06
If you find the time to read my reply to your first post to this thread & you'll see why (the restore script is not working).

Just use the supported script to restore your dB, it is much safer.
Credit where it is due..
I'm fairly sure that more skill, time & careful consideration has gone into crafting those scripts than the replies in this thread.

---

### Post by khPWXxF on 2014-05-06
That's so sensible I fear to butt in but if that fails inexplicably then add the --verbose parameter to get diagnostics.
Phil

---

### Post by itlarson2 on 2014-05-06
Thanks to  			 				 				 					 						 	[**[COLOR=#000000]blm-ubunet[/COLOR]**]("http://ubuntuforums.org/member.php?u=1899844") - he was right, I was trying to run a perl script as a bash scrip, and when I did what he said, the upgrade script ran fine.  The title of this post still applies, though.  The backend still crashes as soon as it starts, and when I run mythtv-setup, I get a repeating "waiting for database schema upgrade lock" message.  Maybe this is because I changed the password for the database?  Here's an excerpt from the backend log:

May  6 21:17:57 jslsll-myth mythbackend: mythbackend[3734]: E CoreContext mythdbcon.cpp:217 (OpenDatabase) Driver error was [1/1045]:#012QMYSQL: Unable to connect#012Database error was:#012Access denied for user 'mythtv'@'localhost' (using password: YES)

how do I make sure the backend knows the right database password?

---

### Post by blm-ubunet on 2014-05-06
If you run mythtv-setup as frontend user named "fe-user" then the dB credentials come from:
/home/fe-user/.mythtv/config.xml

Your typical mythbuntu system has FE & BE running as user "mythtv".

---

### Post by dannyboy79 on 2014-05-06
so basically first check to see if you can access the mythconverg database using username mythtv and the password that's stored within /home/fe-user/.mythtv/config.xml by using the following command
```
mysql -u mythtv -p mythconverg
```
when it prompts for a password use what's inside the config.xml file. if it works than you need to make sure that the config.xml file located at /home/mythtv/.mythtv is the same as /home/fe-user/.mythtv/config.xml as well as checking /etc/mythtv/config.xml. if it doesn't work, there's your problem. you need to ensure the password that mysql for database mythconverg is what's stored within the config.xml file

---

### Post by aelfric55 on 2014-05-07
> **dannyboy79 said:**
> so basically first check to see if you can access the mythconverg database using username mythtv and the password that's stored within /home/fe-user/.mythtv/config.xml by using the following command
```
mysql -u mythtv -p mythconverg
```
when it prompts for a password use what's inside the config.xml file. if it works than you need to make sure that the config.xml file located at /home/mythtv/.mythtv is the same as /home/fe-user/.mythtv/config.xml as well as checking /etc/mythtv/config.xml. if it doesn't work, there's your problem. you need to ensure the password that mysql for database mythconverg is what's stored within the config.xml file

There may also be one under /root/.mythtv/  These are all generally symlinks to the main config.xml under /etc/mythtv/, but sometimes they end up as individual files instead. Not a problem unless they don't match.

---

### Post by dannyboy79 on 2014-05-07
you should never run mythtv-setup as root so there should never be a config.xml located within root's home folder (but as you say it's possible). mythtv-backend is run as user mythtv

---

### Post by itlarson2 on 2014-05-09
Quick update- I have re-installed on a new drive, and should have my data copied over, and the database (hopefully) restored Saturday.  I will do an update post then.

---

### Post by itlarson2 on 2014-05-14
Update:
I got this system working finally.  To successfully update the database I did the following:
-Retrieved the old password for the database off the old failing drive.
-In the new install, I changed the password to old one in the following files:
   /usr/share/mythtv/config.xml
   /etc/mythtv/config.xml
   ~/.mythtv/config.xml

-Changed the password of the current database:
   $ mysql -u root -h localhost -p
   mysql>SET PASSWORD FOR 'mythtv'@'localhost' = PASSWORD('<PASSWORD>');
   mysql> FLUSH PRIVILEGES;
   mysql>quit

-Restored the database:
   mythconverg_restore.pl --drop_database --create_database --filename mythconverg-XXXX

-Edited /etc/mysql/conf.d/mythtv.cnf file to fix an IPV4/IPV6 but that causes the repeating "waiting for database schema upgrade lock" message:
   replace:  bind-address=0.0.0.0
   with:  bind-address= ::

I also had to uncheck "force DPI" in Xfce- it was causing tiny fonts.

---

