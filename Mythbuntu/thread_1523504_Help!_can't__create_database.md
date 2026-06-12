---
title: "Help! can't  create database"
date: 2010-07-03
forum: Mythbuntu
---

### Post by itlarson on 2010-07-03
I have done a clean install and am trying to restore my database.  I have dropped the old database, but I can't create the new one, because I have no idea where it is supposed to go.  Does anyone know the proper location?

---

### Post by itlarson on 2010-07-03
OK  hereis the outputof my attempt to restore the database.  

itl@itlmyth:~/backup$ /usr/share/mythtv/mythconverg_restore.pl --verbose

Configuring environment:
  -    username: itl
  -        HOME: /home/itl
  - MYTHCONFDIR: /home/itl/.mythtv

Parsing configuration files:
  - checking: /home/itl/.mythtv/config.xml
     parsing: /home/itl/.mythtv/config.xml
  - checking: /home/itl/.mythtv/backuprc
     parsing: /home/itl/.mythtv/backuprc

Applying command-line arguments.

Checking configuration.

No filename specified. Attempting to find the newest database backup.
Using database backup file:
/home/itl/backup/mythconverg-1244-20100703152520.sql.gz

WARNING: DBName not specified. Using mythconverg

WARNING: DBHostName not specified.
         Assuming it is specified in the MySQL options file.

WARNING: DBUserName not specified.
         Assuming it is specified in the MySQL options file.

WARNING: DBPassword not specified.
         Assuming it is specified in the MySQL options file.

Database Information:
         DBHostName: 
             DBPort: -1
         DBUserName: 
         DBPassword: 
             DBName: mythconverg
        DBSchemaVer: 
  DBBackupDirectory: /home/itl/backup
   DBBackupFilename: mythconverg-1244-20100703152520.sql.gz
    create_database: 

Executables:
       mysql_client: mysql
         uncompress: gzip -d

Miscellaneous:
    partial_restore: no
   restore_xmltvids: no
    change_hostname: no

Checking database.

Unable to connect to database.
           database: mythconverg
               host: 
           username: 
           password: 

Please check your configuration files to verify the database connection
information is correct.  The files that are used to retrieve connection
information are prefixed with "parsing" in the "Parsing configuration files"
section of the --verbose output.

Also note that any [client] or [mysql] password specified in the MySQL options
file (/etc/my.cnf or /etc/mysql/my.cnf or ~/.my.cnf) will take precedence over
the password specified in the MythTV configuration files.

ERROR: The database does not exist.
itl@itlmyth:~/backup$ 

I am of the belief that I need to create the initial database first for this to work.  Unfortuantly the wiki doesn't specify WHERE to create the database.

---

### Post by jlagrone on 2010-07-03
You do need to create the database. ([http://www.mythtv.org/docs/mythtv-HOWTO-6.html#setupdb](http://www.mythtv.org/docs/mythtv-HOWTO-6.html#setupdb)) This is the command you want:

```
mysql -u root -p < /usr/share/mythtv/sql/mc.sql
```

If you haven't already seen it, this may be of interest as well [http://www.mythtv.org/docs/mythtv-HOWTO-23.html#ss23.5](http://www.mythtv.org/docs/mythtv-HOWTO-23.html#ss23.5)

---

### Post by itlarson on 2010-07-03
Thanks for the quick response!

I tried the command, and it executed without any output.
mythconverg_restore.pl  had the same results.  

I rebooted, but the frontend isn't able to connect to the database at all- it goes int a special setup screen instead of starting normally.

---

### Post by itlarson on 2010-07-03
Question- what is the user supposed to be?  Mythtv, or my user name?

---

### Post by jlagrone on 2010-07-03
It should be mythtv.  Try looking in /home/mythtv/.mythtv/mysql.txt and see if the password is there.  If it's not you can reset it: (this changes it to mythtv)

```
mysql -u root -p mysql
mysql> UPDATE user SET Password=PASSWORD('mythtv') WHERE user='mythtv';
mysql> FLUSH PRIVILEGES;
mysql> quit

```

I had problems connecting when I did a clean install a few months ago.  If I remember correctly the new install generates the mythtv user for mysql and a password, but when you recover the database it puts all the old login information in.  So you have to change everything to the new password.

---

### Post by itlarson on 2010-07-03
Ok- here's what I did:

To drop the database-
$ mysql -u root
mysql> DROP DATABASE IF EXISTS mythconverg;
mysql> quit

to create a new database-
mysql -u root -p < /usr/share/mythtv/sql/mc.sql

to restore the database-
/usr/share/mythtv/mythconverg_restore.pl --verbose

the last item still gives the same result.
I'm not sure what i need to change the password for, since it will be back to the old one after I restore the database.

---

### Post by itlarson on 2010-07-04
/home/itl/.mythtv/config.xml  doesn't exist- Could this be causing the restore program to not know what user the database is for?  maybe you could provide an example of what this file looks like?  I am wondering if the problem is caused by the fact I installed mythtv with my home and storage directories left in place?  Would it work better if I renamed my home directory before installing, and created a new one during the install?  Should my home directory and user  be named mythtv?  Unfortunately I can't continue with this at this time.  I will try to look at it again tomorrow night.

---

### Post by jlagrone on 2010-07-04
I don't think config.xml is necessary.  It looks like the script also looks at the mysql.txt if config.xml is not there.  If the restore script ran fine, it got the proper database settings from somewhere.  On my system I have a config.xml and a mysql.txt in the following places

/home/mythtv/.mythtv/
/home/john/.mythtv/ (my home folder)
/etc/mythtv

The script looks in all these places for either the config.xml or the mysql.txt to get the database settings.  Since the script ran fine for you one of these should exist somewhere and you should be able to use the database name, location, user name, and password to connect.

You might also want to run mythtv-setup and make sure the backend has the correct ip address (or localhost).

---

### Post by itlarson on 2010-07-04
this is from the output mythconverg_restore.pl:

Checking database.

Unable to connect to database.
database: mythconverg
host:
username:
password: 



to me this suggests that its not getting the information it needs.  I have looked at those files and only one of them existed.  I copied it to my home directory and made sure the user was mythtv, but I didn't see anywhere to specify the password.  I am not sure what host means.   Anyway the script output remains the same.

---

### Post by jlagrone on 2010-07-04
Sorry I read that wrong, I thought it was running fine.  I think the simplest thing to do is just create the database and users (or confirm they exits)

from [http://www.mythtv.org/wiki/User_Manual:Initial_Installation#MythTV_database_setup](http://www.mythtv.org/wiki/User_Manual:Initial_Installation#MythTV_database_setup)

Drop mythconverg as before an then recreate it along with an user.  This makes the user be mythtv with a password of mythtv but you could change that if you want.

```

mysql -u root -p
create database mythconverg;
create user 'mythtv'@'%' identified by 'mythtv';
create user 'mythtv'@'localhost' identified by 'mythtv';
set password for 'mythtv'@'%' = password('mythtv');
set password for 'mythtv'@'localhost' = password('mythtv');
connect mythconverg;
grant all privileges on *.* to 'mythtv'@'%' with grant option;
grant all privileges on *.* to 'mythtv'@'localhost' with grant option;
flush privileges;
exit;
```

If you get an error with the create user line, then you already have a mythtv user in mysql.  In that case just change the password to something since you don't currently know what it is.

```
mysql -u root -p mysql
mysql> use mysql;
mysql> UPDATE user SET Password=PASSWORD('mythtv') WHERE user='mythtv';
mysql> FLUSH PRIVILEGES;
mysql> quit
```

Now, create the mysql.txt file.  According to the wiki page it needs to go in ~mythtv/.mythtv/mysql.txt. Change the password if you use something other than mythtv.  I would also move and backup any existing mysql.txt files just to be safe and to prevent the script from finding them instead of the correct one.

```
DBHostName=localhost

# By default, Myth tries to ping the DB host to see if it exists.
# If your DB host or network doesn't accept pings, set this to no:
#
DBHostPing=no

DBHostName=localhost
DBUserName=mythtv
DBName=mythconverg
DBPassword=mythtv

# Set the following if you want to use something other than this
# machine's real hostname for identifying settings in the database.
# This is useful if your hostname changes often, as otherwise you
# will need to reconfigure mythtv (or futz with the DB) every time.
# TWO HOSTS MUST NOT USE THE SAME VALUE
#
LocalHostName=MYCOOLMYTHTVHOST

# If you want your frontend to be able to wake your MySQL server
# using WakeOnLan, have a look at the following settings:
#
#
# The time the frontend waits (in seconds) between reconnect tries.
# This should be the rough time your MySQL server needs for startup
#
#WOLsqlReconnectWaitTime=0
#
#
# This is the number of retries to wake the MySQL server
# until the frontend gives up
#
#WOLsqlConnectRetry=5
#
#
# This is the command executed to wake your MySQL server.
#
#WOLsqlCommand=echo 'WOLsqlServerCommand not set'
```

now you should be able to run the script

---

### Post by itlarson on 2010-07-05
I got it working!  Unfortunately many of my settings were lost, but at least I can watch my programs.  Thanks for all the help.

---

