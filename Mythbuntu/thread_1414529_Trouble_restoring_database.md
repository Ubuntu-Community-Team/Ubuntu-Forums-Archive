---
title: "Trouble restoring database"
date: 2010-02-23
forum: Mythbuntu
---

### Post by Lepy on 2010-02-23
I decided to change my main backend to the 64bit version of mythbunut. On the previous install, I had a cronjob that ran mythconverg_backup.pl and placed the file on my nas.

So, I installed the new version of myth, ran all the updates, setup fstab, and restored my home folder from a backup, but I can't get my database restored.

To set the backup and restore directory, I ran:
```
echo "DBBackupDirectory=/media/pool02/backup/myth/mysql" > ~/.mythtv/backuprc
```

To drop the database from the new install:
```
mysql -uroot -p -e 'DROP DATABASE IF EXISTS mythconverg;'
```

Create new database:
```
mysql -uroot -p< /usr/share/mythtv/sql/mc.sql
```

Log into mysql:
```
mysql -uroot -p mysql
```

Set old password:
```
mysql> UPDATE user SET Password=PASSWORD('ktv9MYA7') WHERE user='mythtv';
mysql> FLUSH PRIVILEGES;

```

Run restore:
```
~/mythstuff/mythconverg_restore.pl
```

But now I only receive "ERROR: The database does not exist."

Initially, I just ran the restore script and got the "ERROR: Unable to do a full restore. The database contains data." I though I followed the wiki to a T, but apparently not. 

Now, even if I run "mysql -uroot -p< /usr/share/mythtv/sql/mc.sql" to create the database, followed by the restore script, I still receive "ERROR: The database does not exist." instead of "ERROR: Unable to do a full restore. The database contains data."

I remember having the exact same issue when I first setup the database scripts and was testing them, but was eventually able to restore. Not sure now...

---

### Post by Lepy on 2010-02-23
Seems using the newest version of the mythconverg_restore.pl with the --verbose tag is much more helpful than the old version I was using.

Seems the script was still accessing the database with the randomly generated password made during the install instead of "mythtv". I changed the password to "mythv" in ~/.mythtv/config.xml, re-ran the script, and everything is back to normal!

---

### Post by myth1914 on 2010-02-25
> **Lepy said:**
> Seems using the newest version of the mythconverg_restore.pl with the --verbose tag is much more helpful than the old version I was using.

Seems the script was still accessing the database with the randomly generated password made during the install instead of "mythtv". I changed the password to "mythv" in ~/.mythtv/config.xml, re-ran the script, and everything is back to normal!

Great to hear it's working, and for adding the solution!  Please mark your thread as resolved.

---

### Post by Lepy on 2010-02-25
Well, I got the database restored successfully, copied over the home backup, and recompiled/reinstalled emulators and programs. So, now the main fe/be has returned to its original configuration, though less cluttered and running snappier...for now.

BUT!!!! Now getting my remote frontend to connect is driving me mad! I changed nothing on the remote fe when I upgraded the main fe/be.

fe/be = xbmc = 192.168.2.100
fe = mythgateway = 192.168.2.107
test fe = lepy =192.168.2.110

The PIN on the backend setup (xbmc) was originally 0000 but was left blank after the database restore, so I set it to 0000 again.

On xbmc, I have commented out bind-address in /etc/mysql/my.cnf
```
#bind-address           = 127.0.0.1

```

I have also added "mysqld: all" to /etc/hosts.allow on xbmc, and both test machines (mythgateway and another laptop that is not a dedicated machine) can access the web interface just fine.

Following Chapter 6 of the docs ([http://www.mythtv.org/docs/mythtv-HOWTO-6.html](http://www.mythtv.org/docs/mythtv-HOWTO-6.html)), I guessed the database restore did not restore MySQL access to my subnet since it was a fresh install. Since none of my passwords were working for root, I reset it to "mythtv" using this guide: [http://www.cyberciti.biz/tips/recover-mysql-root-password.html](http://www.cyberciti.biz/tips/recover-mysql-root-password.html)

Now, "Test MySQL Connection" in the Control Center is successful from the remote machine....but both fes hang at this point

```
lepy@karmic-laptop:~$ mythfrontend.real
2010-02-25 22:32:20.018 mythfrontend version: branches/release-0-22-fixes [22594] www.mythtv.org
2010-02-25 22:32:20.047 AudioPulseUtil: Suspend Success
2010-02-25 22:32:20.047 Using runtime prefix = /usr
2010-02-25 22:32:20.047 Using configuration directory = /home/lepy/.mythtv
2010-02-25 22:32:20.049 MediaRenderer::HttpServer Create Error

```

and still

```
lepy@karmic-laptop:~$ mysql --user=mythtv --password=mythtv mythconverg
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
```

I think I've provided too much information, but I have been searching all over for an answer. Long story short, the upgrade to 64 bit went great for the fe/be just not anything that wants to connect to it! I guess the MySQL access issue is sorted out...but why are both frontends hanging with the same error?

Here is relevant info and log clips:

Backend Setup -> General

local backend (xbmc)
ip: 192.168.2.100
port: 6543 status port: 6544
security pin: 0000

master backend
ip: 192.168.2.100 port: 6543

```
xbmc@xbmc:~$ mysql --user=mythtv --password=mythtv mythconverg
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 219
Server version: 5.1.37-1ubuntu5.1 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> 
```

```
mythgateway@mythgateway-laptop:~$ mysql --user=mythtv --password=mythtv mythconverg
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
```

```
xbmc@xbmc:~$ mythfrontend.real
2010-02-25 20:53:10.224 mythfrontend version: branches/release-0-22-fixes [22594] www.mythtv.org
2010-02-25 20:53:10.235 Using runtime prefix = /usr
2010-02-25 20:53:10.235 Using configuration directory = /home/xbmc/.mythtv
2010-02-25 20:53:10.768 Empty LocalHostName.
2010-02-25 20:53:10.768 Using localhost value of xbmc
2010-02-25 20:53:10.772 New DB connection, total: 1
2010-02-25 20:53:10.774 Connected to database 'mythconverg' at host: localhost
2010-02-25 20:53:10.775 Closing DB connection named 'DBManager0'
2010-02-25 20:53:10.781 ScreenSaverX11Private: Gnome screen saver support enabled
2010-02-25 20:53:10.782 DPMS is active.
2010-02-25 20:53:10.782 Primary screen: 0.
2010-02-25 20:53:10.782 Connected to database 'mythconverg' at host: localhost
2010-02-25 20:53:10.783 Using screen 0, 1296x780 at 0,0
Then normal boot stuff, it works, have access to database and can watch shows
```

```
mythgateway@mythgateway-laptop:~$ mythfrontend.real
2010-02-25 21:04:33.128 mythfrontend version: branches/release-0-22-fixes [22594] www.mythtv.org
2010-02-25 21:04:33.144 Using runtime prefix = /usr
2010-02-25 21:04:33.144 Using configuration directory = /home/mythgateway/.mythtv
2010-02-25 22:32:20.049 MediaRenderer::HttpServer Create Error

```

xbmc /etc/mythtv/config.xml
```
onfiguration>
  <UPnP>
    <MythFrontend>
      <DefaultBackend>
        <DBHostName>localhost</DBHostName>
        <DBUserName>mythtv</DBUserName>
        <DBPassword>WJq1Nb2K</DBPassword>
        <DBName>mythconverg</DBName>
        <DBPort>0</DBPort>
      </DefaultBackend>
    </MythFrontend>
  </UPnP>
</Configuration>

```

mythgateway /etc/mythtv/config.xml
```
<Configuration>
  <UPnP>
    <MythFrontend>
      <DefaultBackend>
        <DBHostName>192.168.2.100</DBHostName>
        <DBUserName>mythtv</DBUserName>
        <DBPassword>mythtv</DBPassword>
        <DBName>mythconverg</DBName>
        <DBPort>6543</DBPort>
      </DefaultBackend>
    </MythFrontend>
  </UPnP>
</Configuration>

```

xbmc /etc/mythtv/mysql.txt
```
DBHostName=localhost

# By default, Myth tries to ping the DB host to see if it exists.
# If your DB host or network doesn't accept pings, set this to no:
#
#DBHostPing=no

DBUserName=mythtv
DBPassword=mythtv
DBName=mythconverg
DBType=QMYSQL3

```

mythgateway /etc/mythtv/mysql.txt
```
DBHostName=192.168.2.100

# By default, Myth tries to ping the DB host to see if it exists.
# If your DB host or network doesn't accept pings, set this to no:
#
#DBHostPing=no

DBUserName=mythtv
DBPassword=mythtv
DBName=mythconverg
DBType=QMYSQL3

```

On each machine, these files have the exact same corresponding information shown above:
/home/mythtv/.mythtv/config.xml
/home/mythtv/.mythtv/mysql.txt

/home/xbmc/.mythtv/mysql.txt
```
DBHostName=localhost

# By default, Myth tries to ping the DB host to see if it exists.
# If your DB host or network doesn't accept pings, set this to no:
#
#DBHostPing=no

DBUserName=mythtv
DBPassword=mythtv
DBName=mythconverg
DBType=QMYSQL3

```

/home/xbmc/.mythtv/config.xml
```
<Configuration>
  <UPnP>
    <UDN>
      <MediaRenderer>3934bfee-39cb-48c3-9ce6-fed80ba8bda8</MediaRenderer>
    </UDN>
    <MythFrontend>
      <DefaultBackend>
        <DBHostName>localhost</DBHostName>
        <DBUserName>mythtv</DBUserName>
        <DBPassword>mythtv</DBPassword>
        <DBName>mythconverg</DBName>
        <DBPort>0</DBPort>
      </DefaultBackend>
    </MythFrontend>
  </UPnP>
</Configuration>

```

/home/mythgateway/.mythtv/mysql.txt
```
DBHostName=192.168.2.100

# By default, Myth tries to ping the DB host to see if it exists.
# If your DB host or network doesn't accept pings, set this to no:
#
#DBHostPing=no

DBPort=6543
DBUserName=mythtv
DBPassword=mythtv
DBName=mythconverg
DBType=QMYSQL3

```

/home/mythgateway/.mythtv/config.xml
```
<Configuration>
  <UPnP>
    <UDN>
      <MediaRenderer>7808073c-5a1b-4cc2-b39a-c0152e514a73</MediaRenderer>
    </UDN>
    <MythFrontend>
      <DefaultBackend>
        <DBHostName>192.168.2.100</DBHostName>
        <DBUserName>mythtv</DBUserName>
        <DBPassword>mythtv</DBPassword>
        <DBName>mythconverg</DBName>
        <DBPort>6543</DBPort>
      </DefaultBackend>
    </MythFrontend>
  </UPnP>
</Configuration>

```

---

### Post by Lepy on 2010-02-25
And I just tried running mythfrontend.real from the test fe and it got a bit further

```
lepy@karmic-laptop:~$ mythfrontend.real 
2010-02-25 22:49:32.169 mythfrontend version: branches/release-0-22-fixes [22594] www.mythtv.org
2010-02-25 22:49:32.195 AudioPulseUtil: Suspend Success
2010-02-25 22:49:32.195 Using runtime prefix = /usr
2010-02-25 22:49:32.196 Using configuration directory = /home/lepy/.mythtv
2010-02-25 22:49:32.197 MediaRenderer::HttpServer Create Error
2010-02-25 22:49:32.198 Empty LocalHostName.
2010-02-25 22:49:32.198 Using localhost value of karmic-laptop
2010-02-25 22:49:32.198 Testing network connectivity to '192.168.2.100'
2010-02-25 22:49:32.219 New DB connection, total: 1

```

Test MySQL Connection in Control Center using
user - mythtv
pass -mythtv
database - mythconverg
server - 192.168.2.100

still reports success...but no remote fe love! I just want to watch some TV!!! :popcorn:

---

### Post by Lepy on 2010-02-26
I've spent a little more time and finally have the frontends connecting to the main fe/be.

I think that the main problem was the port being used. The test connection in control centre worked but the fe would not connect successfully. I used Port Scan in Network Tools to scan the main be and found the relevant ports 3306 (open mysql), 6543 (open unknown), 6544 (open unknown), 6547 (open unknown). 

From mythtv-setup on the be, I had the port set to 6543...it should be using that port, right? Wrong! On a whim, I changed the DBPort=6543 in all the config files to DBPort=3306, and the frontends will connect now.

The connections seem to be a tad slower than they were before the be upgrade to 64 bit, maybe because I am now connecting to the database using the default mysql port instead of a dedicated mythtv mysql port? 

Also, randomly when running mythfrontend.real -v all, the fe will hang at MediaRenderer::HttpServer Create Error. Cancelling and running again once or multiple times will finally make it boot into the frontend interface. This could potentially cause problems when the fe first boots up or woken from suspend. Anyone now why this is happening?

I'm just really confused as to what could have gone so terribly wrong during the database restore that the port specified in mythtv-setup seems to be completely ignored. Things are working now...but I'm concerned about upgrades in the future and not sure if trying a fresh restore would fix anything.

In my previous post I was not using the -h <ip> variable in the mysql command from the remote fe. Doh!

---

### Post by Erden on 2010-12-07
Hello,

My harddrive crashed. I hardly recovered /var/lib/mtytv folder. I have my database. I installed a fresh copy of Ubuntu 10.04 and Mythtv 0.23. 

I followed the instructions in the first message.

Database is restored successfully. However, when I open the frontend it asks me to chose the language and it says: 

```
"This version of MythTV requires an updated database. (schema is 1254).

Please run mythtv-setup or mythbackend to update your database.

Database host: localhost
Database name: mythconverg"
```

When I run either of those I chose upgrade option (to 1254) it exits and asks for running mythfilldatabase. When I run it it also gives the same message about updated database.

Any help would be appreciated!

---

