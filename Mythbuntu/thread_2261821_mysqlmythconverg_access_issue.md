---
title: "mysql/mythconverg access issue"
date: 2015-01-21
forum: Mythbuntu
---

### Post by nainsurvolte on 2015-01-21
I am rebuilding a mythbuntu after having some weird problem for some time and after getting some migration issues passing from 12.04 to 14.04.

Everything is going well up until I tried to restore my database that I backed up before doing all the rebuilding work.

I first tried to do a partial restore. The installation of mythbuntu had created the database. after reading on the mythtv wiki what was a full/partial restore, I figured out that it was the way to go for me. In my last database, I had character set issues which I could not resolve, hence importing only the data to a fresh mythtv install seamed the way to go (may I say that I was on mythtv 0.27 latest update when I backed up and I presume that so was the fresh mythtv since it is 0.27 latest update). 

It all worked fine except for two things. One for some reason it did not operate the scheduling (had to select them one by one and then apply changes to make them recognize next recording). Two, all the current recordings although listed, were not linked to the files on the drives. I decided to drop the database and try a full restore to see the result. Problem one was solved but not 2. I checked the information linked to the recordings to see what could be the problem and  found out their was a difference between my definition of the recording group in the past and now. I realigned editing them through backend and deleting the bad one through phpmyadmin interface (could not found how to do so in mythbackend).

This is when it started to act weird...

I did another import, and got access problem. The mythconverg_restore.pl tells me that it has password issue. I went to see the default password in the config.xml. I thought changing it might be it. I got in mysql, change the password for all mythtv user declaration in the table list. I then changed the password in the config.xml to match that new one. I tested that new password logging in to mythconverg database as mythtv, all good.

That changed nothing. I still get that connection to database issue. I made a search for any config.xml or any my.cnf (or as mentioned in the error message) to see if a password to connect to mysql or mythconverg could be declared. Nothing.

I am out of option and ideas. As mentioned, connecting to the database is not a problem, testing the connection gives a green check, logging in through phpmyadmin works, logging in using a terminal window through command line works all using mythtv user and that new password (same as in the previous install). Finally, I use the --verbose mode when trying to restore, and it does use that same password that I am using successfully by other means.

If you believe you can help but need additional information (config file, error message etc.) let me know. I usually post them  with the problem description, but I am actually on my Win7 machine and the VNC configuration is not done yet.

Thanks,

---

### Post by tgm4883 on 2015-01-21
> **nainsurvolte said:**
> I am rebuilding a mythbuntu after having some weird problem for some time and after getting some migration issues passing from 12.04 to 14.04.

Everything is going well up until I tried to restore my database that I backed up before doing all the rebuilding work.

I first tried to do a partial restore. The installation of mythbuntu had created the database. after reading on the mythtv wiki what was a full/partial restore, I figured out that it was the way to go for me. In my last database, I had character set issues which I could not resolve, hence importing only the data to a fresh mythtv install seamed the way to go (may I say that I was on mythtv 0.27 latest update when I backed up and I presume that so was the fresh mythtv since it is 0.27 latest update). 

It all worked fine except for two things. One for some reason it did not operate the scheduling (had to select them one by one and then apply changes to make them recognize next recording). Two, all the current recordings although listed, were not linked to the files on the drives. I decided to drop the database and try a full restore to see the result. Problem one was solved but not 2. I checked the information linked to the recordings to see what could be the problem and  found out their was a difference between my definition of the recording group in the past and now. I realigned editing them through backend and deleting the bad one through phpmyadmin interface (could not found how to do so in mythbackend).

This is when it started to act weird...

I did another import, and got access problem. The mythconverg_restore.pl tells me that it has password issue. I went to see the default password in the config.xml. I thought changing it might be it. I got in mysql, change the password for all mythtv user declaration in the table list. I then changed the password in the config.xml to match that new one. I tested that new password logging in to mythconverg database as mythtv, all good.

That changed nothing. I still get that connection to database issue. I made a search for any config.xml or any my.cnf (or as mentioned in the error message) to see if a password to connect to mysql or mythconverg could be declared. Nothing.

I am out of option and ideas. As mentioned, connecting to the database is not a problem, testing the connection gives a green check, logging in through phpmyadmin works, logging in using a terminal window through command line works all using mythtv user and that new password (same as in the previous install). Finally, I use the --verbose mode when trying to restore, and it does use that same password that I am using successfully by other means.

If you believe you can help but need additional information (config file, error message etc.) let me know. I usually post them  with the problem description, but I am actually on my Win7 machine and the VNC configuration is not done yet.

Thanks,

If you run the restore with --verbose it should tell you what config file it's looking at. Should look something like this

```
tmashos@tmashos-wks:~$ /usr/share/mythtv/mythconverg_restore.pl --verbose

Configuring environment:
  -    username: tmashos
  -        HOME: /home/tmashos
  - MYTHCONFDIR: /home/tmashos/.mythtv

Parsing configuration files:
  - checking: /home/tmashos/.mythtv/config.xml
     parsing: /home/tmashos/.mythtv/config.xml
  - checking: /home/tmashos/.mythtv/backuprc

Applying command-line arguments.

Checking configuration.

Database Information:
         DBHostName: localhost
             DBPort: 3306
         DBUserName: mythtv
         DBPassword: XXX
             DBName: mythconverg
        DBSchemaVer: 
  DBBackupDirectory: 
   DBBackupFilename: 
      drop_database: no
    create_database: no

Executables:
       mysql_client: mysql
         uncompress: gzip -d

Miscellaneous:
    partial_restore: no
   restore_xmltvids: no
    change_hostname: no

ERROR: DBBackupDirectory not specified, stopped at /usr/share/mythtv/mythconverg_restore.pl line 773.

```

---

### Post by nainsurvolte on 2015-01-21
Same as yours, in */home/"my user name"/.mythtv*.

But password and user name are the same as I am using everywhere.

I will log from my Linux machine and post some more information such as error I get and config file.

---

### Post by nainsurvolte on 2015-01-21
here is the command line I am trying to use, expecting to drop the database (due to the error generated when importing), create the database and import the backup...

```
./mythconverg_restore.pl --verbose --drop_database --create_database --directory /home/owner --filename mythconverg-1317-20150119195507.sql.gz
```

Here is the config.xml file that is parsed

```
<Configuration>  <Database>
    <PingHost>1</PingHost>
    <Host>127.0.0.1</Host>
    <UserName>mythtv</UserName>
    <Password>[password]</Password>
    <DatabaseName>mythconverg</DatabaseName>
    <Port>3306</Port>
  </Database>
  <WakeOnLAN>
    <Enabled>0</Enabled>
    <SQLReconnectWaitTime>0</SQLReconnectWaitTime>
    <SQLConnectRetry>5</SQLConnectRetry>
    <Command>echo 'WOLsqlServerCommand not set'</Command>
  </WakeOnLAN>
  <LocalHostName></LocalHostName>
</Configuration>
```

And the password I use is good. I can log in the database using that password following that command line:

```
mysql -u mythtv -p mythconverg 
```

and the same using phpmyadmin from my Win7 PC.

Following that, here is the information in the terminal window when running the script

```
Configuring environment:  -    username: owner
  -        HOME: /home/owner
  - MYTHCONFDIR: /home/owner/.mythtv


Parsing configuration files:
  - checking: /home/owner/.mythtv/config.xml
     parsing: /home/owner/.mythtv/config.xml
  - checking: /home/owner/.mythtv/backuprc


Applying command-line arguments.


Checking configuration.


Database Information:
         DBHostName: 127.0.0.1
             DBPort: 3306
         DBUserName: mythtv
         DBPassword: XXX
             DBName: mythconverg
        DBSchemaVer: 
  DBBackupDirectory: /home/owner
   DBBackupFilename: mythconverg-1317-20150119195507.sql.gz
      drop_database: yes
    create_database: yes


Executables:
       mysql_client: mysql
         uncompress: gzip -d


Miscellaneous:
    partial_restore: no
   restore_xmltvids: no
    change_hostname: no


Checking database.


Preparing initial database.
Dropping database.
Creating database.
Setting database character set.


Found 0 tables in the database.


Backup file is compressed.
 - Uncompressing backup file with IO::Uncompress::Gunzip.


Attempting to use supplied password for mysql command-line client.
Any [client] or [mysql] password specified in the MySQL options file will
take precedence.


Executing command:
'mysql' --defaults-extra-file='/tmp/1MepRFlmcg' --host='127.0.0.1' --port='3306' --user='mythtv' 'mythconverg'
ERROR 1062 (23000) at line 1885: Duplicate entry '&#65533;?mile et Mila' for key 'PRIMARY'


ERROR: Cannot write to mysql, stopped at ./mythconverg_restore.pl line 1720, <BACKUP> line 1939.

```

The worst now is that my mythbackend does not start anymore... as it does not seem to be able to connect to anymore. And the Test connection is still green.

:confused:

---

### Post by nainsurvolte on 2015-01-21
Things went a bit further now...

In another post ( this one [http://ubuntuforums.org/showthread.php?t=790814](http://ubuntuforums.org/showthread.php?t=790814)) somebody suggested to run this command:

```
[COLOR=#000000]*sudo dpkg-reconfigure mythtv-database*[/COLOR]
```

After that, I ran a partial restore and it seem to work (no error message).

But now, I have a problem going in through mythweb. And somewhere deep in the error message I receive when trying to connect I recongnize that it is using the default password there was after the installation (db_password).

When going through the Database.php file used by mythweb, it calls for the database name, user and password. But where does he gets it? Could it be loaded in memory? This is where that darn default password is hidden and making trouble and it ain't any of the config.xml for the database.

:|

---

### Post by nainsurvolte on 2015-01-21
Here... 

[http://www.gossamer-threads.com/lists/mythtv/users/524583](http://www.gossamer-threads.com/lists/mythtv/users/524583)

Solved....

---

