---
title: "&quot;Myth cannot connect to the database&quot;"
date: 2007-11-04
forum: Mythbuntu
---

### Post by pasta514 on 2007-11-04
Today I installed Edubuntu 7.10 i386 followed by mythbuntu 7.10.
I've never run mythtv before, so not exactly sure what I'm looking for.
This system I'm setting up as a backend, but while I'm setting it up I want to debug it as the frontend also, I do not have easy access to my true front-end machine yet.

When I run frontend it takes me to the 'database configuration' screen showing the error 'myth cannot connect to the database.

Questions: 
1) what should the root mysql password be?  blank, same as a login or root password, or something entirely independent?
2) how about the user password for user mythtv?



Here are some of the output I get trying to debug this:

-------------------------------------------------------------------------------------------
papa@sipper:/etc/init.d$ sudo ./mysql restart
 * Stopping MySQL database server mysqld                                 [ OK ] 
 * Starting MySQL database server mysqld                                 [ OK ] 
 * Checking for corrupt, not cleanly closed and upgrade needing tables.
papa@sipper:/etc/init.d$ 


-------------------------------------------------------------------------------------------
papa@sipper:/etc/init.d$ ps -p 7416
  PID TTY          TIME CMD
 7416 pts/3    00:00:00 mysqld
papa@sipper:/etc/init.d$ 



-------------------------------------------------------------------------------------------
papa@sipper:~$ ps -p `cat /var/run/mythtv/mythbackend.pid`
  PID TTY          TIME CMD
:confused:


-------------------------------------------------------------------------------------------
papa@sipper:/etc/init.d$ sudo ./mythtv-backend restart
Restarting MythTV server: mythbackend No /usr/bin/mythbackend found running; none killed.:confused:
.
.
papa@sipper:/etc/init.d$ sudo ./mythtv-backend start
mythbackend already running, use restart instead.
papa@sipper:/etc/init.d$ sudo ./mythtv-backend restart
Restarting MythTV server: mythbackend No /usr/bin/mythbackend found running; none killed.
.
.
papa@sipper:/etc/init.d$ sudo ./mythtv-backend restart
Restarting MythTV server: mythbackend No /usr/bin/mythbackend found running; none killed.
.
.
papa@sipper:/etc/init.d$ 

-------------------------------------------------------------------------------------------
papa@sipper:~$ more /var/log/mythtv/mythbackend.log
2007-11-03 19:15:21.370 Using runtime prefix = /usr
2007-11-03 19:15:21.395 New DB connection, total: 1
2007-11-03 19:15:21.416 Unable to connect to database!
2007-11-03 19:15:21.421 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES):confused:

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-11-03 19:15:21.485 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-11-03 19:15:21.546 Failed to init MythContext, exiting.
2007-11-03 19:25:36.360 Using runtime prefix = /usr
2007-11-03 19:25:36.392 New DB connection, total: 1
2007-11-03 19:25:36.401 Unable to connect to database!
2007-11-03 19:25:36.401 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-11-03 19:25:36.454 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-11-03 19:25:36.505 Failed to init MythContext, exiting.
2007-11-03 19:30:36.239 Using runtime prefix = /usr
2007-11-03 19:30:36.573 New DB connection, total: 1
2007-11-03 19:30:36.601 Unable to connect to database!
2007-11-03 19:30:36.652 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-11-03 19:30:36.724 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-11-03 19:30:36.781 Failed to init MythContext, exiting.
2007-11-03 19:33:23.125 Using runtime prefix = /usr
2007-11-03 19:33:23.161 New DB connection, total: 1
2007-11-03 19:33:23.170 Unable to connect to database!
2007-11-03 19:33:23.171 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-11-03 19:33:23.223 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-11-03 19:33:23.274 Failed to init MythContext, exiting.
2007-11-03 19:50:59.297 Using runtime prefix = /usr
2007-11-03 19:50:59.625 New DB connection, total: 1
2007-11-03 19:50:59.636 Unable to connect to database!
2007-11-03 19:50:59.637 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-11-03 19:50:59.714 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-11-03 19:50:59.780 Failed to init MythContext, exiting.
2007-11-03 20:12:24.645 Using runtime prefix = /usr
2007-11-03 20:12:24.691 New DB connection, total: 1
2007-11-03 20:12:24.711 Unable to connect to database!
2007-11-03 20:12:24.712 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-11-03 20:12:24.765 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-11-03 20:12:24.816 Failed to init MythContext, exiting.
2007-11-03 20:13:57.060 Using runtime prefix = /usr
2007-11-03 20:13:57.096 New DB connection, total: 1
2007-11-03 20:13:57.105 Unable to connect to database!
2007-11-03 20:13:57.119 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-11-03 20:13:57.175 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-11-03 20:13:57.226 Failed to init MythContext, exiting.
2007-11-03 20:28:55.123 Using runtime prefix = /usr
2007-11-03 20:28:55.147 New DB connection, total: 1
2007-11-03 20:28:55.156 Unable to connect to database!
2007-11-03 20:28:55.157 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-11-03 20:28:55.210 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-11-03 20:28:55.261 Failed to init MythContext, exiting.
2007-11-03 20:38:48.772 Using runtime prefix = /usr
2007-11-03 20:38:48.806 New DB connection, total: 1
2007-11-03 20:38:48.815 Unable to connect to database!
2007-11-03 20:38:48.815 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2007-11-03 20:38:48.868 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2007-11-03 20:38:48.919 Failed to init MythContext, exiting.


Thanks!

---

### Post by superm1 on 2007-11-04
Did you previously have mysql installed?

Please see [http://ubuntuforums.org/showpost.php?p=3691155&postcount=4](http://ubuntuforums.org/showpost.php?p=3691155&postcount=4)

For some debugging  tips.

---

### Post by pasta514 on 2007-11-04
This was a clean install of edubuntu 7.10, so I don't think that installed mysql, but I don't know.

The mythbuntu install was not exactly painless; I had to manually install some (one) of the packages.  I think there were issues with repositories, but I wouldn't think that would cause this problem.  

After edubuntu installed and was brought currnet the process I followed was:
1) install mythbuntu from [http://www.mythbuntu.org/existing-ubuntu](http://www.mythbuntu.org/existing-ubuntu)
1a) track down and install mythtv-common
2) install the AMD64 patch to get control centre working
3) run control centre - SUCCESS:)
3a) enable 'primary backend' as backend role; apply changes
3a) enable frontend' as frontend role; apply changes
4) Run Frontend... now cannot get past problems already noted:(

I have also tried all the steps in your recommended link without success.  Do you need to see the output from that?

Thanks,

---

### Post by superm1 on 2007-11-04
> **pasta514 said:**
> This was a clean install of edubuntu 7.10, so I don't think that installed mysql, but I don't know.

The mythbuntu install was not exactly painless; I had to manually install some (one) of the packages.  I think there were issues with repositories, but I wouldn't think that would cause this problem.  

After edubuntu installed and was brought currnet the process I followed was:
1) install mythbuntu from [http://www.mythbuntu.org/existing-ubuntu](http://www.mythbuntu.org/existing-ubuntu)
1a) track down and install mythtv-common
2) install the AMD64 patch to get control centre working
3) run control centre - SUCCESS:)
3a) enable 'primary backend' as backend role; apply changes
3a) enable frontend' as frontend role; apply changes
4) Run Frontend... now cannot get past problems already noted:(

I have also tried all the steps in your recommended link without success.  Do you need to see the output from that?

Thanks,

Yes output would be good.  You sure you haven't skipped any steps in what you did here to install?   Where did you get mythtv-common from?  Its in multiverse, so when you installed from the website, as long as you followed those prerequisites, it would have been installable.

---

### Post by pasta514 on 2007-11-04
> **superm1 said:**
> Yes output would be good.  You sure you haven't skipped any steps in what you did here to install?   Where did you get mythtv-common from?  Its in multiverse, so when you installed from the website, as long as you followed those prerequisites, it would have been installable.

I got mythtv-common from here:
[http://www.debian-multimedia.org/dists/testing/main/binary-alpha/package/mythtv-common.php](http://www.debian-multimedia.org/dists/testing/main/binary-alpha/package/mythtv-common.php)

then later I added the repository
  [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
uninstalled the debian package and installed it from the synaptic package manager

> rm ~/.mythtv -rf && rm /home/mythtv/.mythtv -rf
no issues

> sudo dpkg-reconfigure mythtv-database
is localhost OK?
>                 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring mythtv-database &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;                 
                &#9474;                                             &#9474;                 
                &#9474;                                             &#9474;                 
                &#9474; On what host does the MySQL server reside:  &#9474;                 
                &#9474;                                             &#9474;                 
                &#9474; localhost__________________________________ &#9474;                 
                &#9474;                                             &#9474;                 
                &#9474;                   <Ok>  


>   &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring mythtv-database &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
  &#9474; This information will be used to create a database and user for MythTV.  &#9474;  
  &#9474;                                                                          &#9474;  
  &#9474; Unless you have explicitly changed this on the MySQL server, and         &#9474;  
  &#9474; understand MySQL's privilege system, use the default of 'root'.          &#9474;  
  &#9474;                                                                          &#9474;  
  &#9474; What is the name of the MySQL administrator account:                     &#9474;  
  &#9474;                                                                          &#9474;  
  &#9474; root____________________________________________________________________ &#9474;  
  &#9474;                                                                          &#9474;  
  &#9474;                                  <Ok>                                    &#9474;  
  &#9474;         


>   &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring mythtv-database &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
  &#9474; This information will be used to create a database and user for MythTV.  &#9474;  
  &#9474;                                                                          &#9474;  
  &#9474; Unless you have explicitly changed the password on the MySQL server,     &#9474;  
  &#9474; leave this blank.                                                        &#9474;  
  &#9474;                                                                          &#9474;  
  &#9474; What is the password for the MySQL administrator account 'root':         &#9474;  
  &#9474;                                                                          &#9474;  
  &#9474; ________________________________________________________________________ &#9474;  
  &#9474;                                                                          &#9474;  
  &#9474;                                  <Ok>                                    &#9474;  
 

I left the password blank.  Previously I tried setting it to non-blank, but that didn't seem to work either.

> &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring mythtv-database &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474;                                                                           &#9474;  
 &#9474; If you will be using any other computers (that includes other Front End   &#9474;  
 &#9474; machines) with MythTV, this computer needs to be configured to allow      &#9474;  
 &#9474; remote connections. Do you want to enable remote connectivity?            &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; Note that this is a security risk, as both the MythTV and MySQL services  &#9474;  
 &#9474; will be exposed. Be sure to place this machine behind a firewall.         &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; If you have multiple interfaces, the first one listed in 'ifconfig' will  &#9474;  
 &#9474; be used.                                                                  &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; Will you be using other computers running MythTV?                         &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474;                    <Yes>                       <No>                       &#9474;  
 &#9474;  

I answered YES

> papa@sipper:~$ rm ~/.mythtv -rf && rm /home/mythtv/.mythtv -rf
papa@sipper:~$ sudo dpkg-reconfigure mythtv-database
[sudo] password for papa:
Failed to connect to database: Access denied for user 'root'@'localhost' (using password: YES) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
It's also possible that mysql-server wasn't running.  After install
is completed, you will need to make sure mysql-server is running
and that you supplied correct information. Try:
sudo dpkg-reconfigure mythtv-database
papa@sipper:~$ 


> sudo dpkg-reconfigure mythtv-common

>        &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring mythtv-common &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;       
       &#9474; If a database with this name already exists, it will be used.  &#9474;       
       &#9474;                                                                &#9474;       
       &#9474; What database should be used to hold MythTV data:              &#9474;       
       &#9474;                                                                &#9474;       
       &#9474; mythconverg___________________________________________________ &#9474;       
       &#9474;                                                                &#9474;       
       &#9474;                             <Ok>                               &#9474;       
       &#9474;                                                                &#9474;       
   

>   &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring mythtv-common &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
  &#9474; This user will automatically be granted appropriate permissions to the   &#9474;  
  &#9474; database.                                                                &#9474;  
  &#9474;                                                                          &#9474;  
  &#9474; What username should MythTV use to access its database:                  &#9474;  
  &#9474;                                                                          &#9474;  
  &#9474; mythtv__________________________________________________________________ &#9474;  
  &#9474;                                                                          &#9474;  
  &#9474;                                  <Ok>                                    &#9474;  
 

>       &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring mythtv-common &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;       
      &#9474; If you give an empty password, a random one will be generated.  &#9474;       
      &#9474;                                                                 &#9474;       
      &#9474; What password should MythTV use to access its database:         &#9474;       
      &#9474;                                                                 &#9474;       
      &#9474; _______________________________________________________________ &#9474;       
      &#9474;                                                                 &#9474;       
      &#9474;                             <Ok>                                &#9474;       
 

I put in password mythtv

>                 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring mythtv-common &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;                 
                &#9474;                                             &#9474;                 
                &#9474;                                             &#9474;                 
                &#9474; On what host does the MySQL server reside:  &#9474;                 
                &#9474;                                             &#9474;                 
                &#9474; localhost__________________________________ &#9474;                 
                &#9474;                                             &#9474;                 
                &#9474;                   <Ok>                      &#9474;                 
 
> papa@sipper:~$ sudo dpkg-reconfigure mythtv-common
[sudo] password for papa:
papa@sipper:~$ 



After all this I again tried to run the frontend without any success or changes in behavior.

Thanks,

---

### Post by superm1 on 2007-11-04
> **pasta514 said:**
> I got mythtv-common from here:
[http://www.debian-multimedia.org/dists/testing/main/binary-alpha/package/mythtv-common.php](http://www.debian-multimedia.org/dists/testing/main/binary-alpha/package/mythtv-common.php)

then later I added the repository
  [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
uninstalled the debian package and installed it from the synaptic package manager


no issues


is localhost OK?








I left the password blank.  Previously I tried setting it to non-blank, but that didn't seem to work either.



I answered YES











I put in password mythtv





After all this I again tried to run the frontend without any success or changes in behavior.

Thanks,

Your problem is from mixing and matching debian multimedia and ubuntu repositories.  They are NOT compatible.  We do significantly different things.

Here is the easiest solution.

1) Enable Universe and Multiverse as described on mythbuntu.org/existing-ubuntu.

2) Disable debian multimedia if it is still enabled.

3) Open up synaptic.  "Completely Remove" all myth* packages.

4) Completely remove mysql-server-5.0 mysql-server

5) sudo rm /home/mythtv ~/.mythtv /etc/mythtv -rf

6) Reinstall from mythbuntu control centre

---

### Post by pasta514 on 2007-11-04
> Here is the easiest solution.

1) Enable Universe and Multiverse as described on mythbuntu.org/existing-ubuntu.

2) Disable debian multimedia if it is still enabled.

3) Open up synaptic. "Completely Remove" all myth* packages.

4) Completely remove mysql-server-5.0 mysql-server

5) sudo rm /home/mythtv ~/.mythtv /etc/mythtv -rf

6) Reinstall from mythbuntu control centre

I followed your instructions without success.

Then I did it again, adding the following steps:
5.5) sudo apt-get clean
5.6) reboot (from my windows days)
This time it downloaded all fresh packages

Unfortunately, no luck.  I successfully installed the control centre, then assigned this machine to be backend.  Here is the message I got: (same as before). 

> MythTV-Database reconfigure required

The mythtv-database package was upgraded or installed, but was unable to contact a MySQL server.
If you were in the process of dist-upgrading, this is normal as mysql-server is stopped for a portion of the upgrade.
If this is a fresh package installation, verify that mysql-server is installed and running.  Once you have verified the server is running, you can reconfigure the package by running 'sudo dpkg-reconfigure mythtv-database'.
If your root password or location of the MySQL server are non standard, you can also update them via 'sudo dpkg-reconfigure mythtv-database'.

> papa@sipper:~$ sudo ps -A
[sudo] password for papa:
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 migration/1
    7 ?        00:00:00 ksoftirqd/1
    8 ?        00:00:00 watchdog/1
    9 ?        00:00:00 events/0
   10 ?        00:00:00 events/1
   11 ?        00:00:00 khelper
   31 ?        00:00:00 kblockd/0
   32 ?        00:00:00 kblockd/1
   33 ?        00:00:00 kacpid
   34 ?        00:00:00 kacpi_notify
  179 ?        00:00:00 kseriod
  207 ?        00:00:00 pdflush
  208 ?        00:00:00 pdflush
  209 ?        00:00:00 kswapd0
  260 ?        00:00:00 aio/0
  261 ?        00:00:00 aio/1
 1331 ?        00:00:00 ksnapd
 2209 ?        00:00:00 ksuspend_usbd
 2210 ?        00:00:00 khubd
 2238 ?        00:00:00 ata/0
 2239 ?        00:00:00 ata/1
 2305 ?        00:00:00 ata_aux
 2443 ?        00:00:00 scsi_eh_0
 2444 ?        00:00:00 scsi_eh_1
 2445 ?        00:00:00 scsi_eh_2
 2446 ?        00:00:00 scsi_eh_3
 2808 ?        00:00:00 kjournald
 3014 ?        00:00:00 udevd
 4044 ?        00:00:00 kpsmoused
 4301 ?        00:00:00 cx88 tvaudio
 4683 ?        00:00:00 kjournald
 4920 tty4     00:00:00 getty
 4921 tty5     00:00:00 getty
 4925 tty2     00:00:00 getty
 4927 tty3     00:00:00 getty
 4928 tty1     00:00:00 getty
 4929 tty6     00:00:00 getty
 5114 ?        00:00:00 acpid
 5164 ?        00:00:00 kondemand/0
 5165 ?        00:00:00 kondemand/1
 5227 ?        00:00:00 syslogd
 5284 ?        00:00:00 dd
 5286 ?        00:00:00 klogd
 5307 ?        00:00:00 dbus-daemon
 5323 ?        00:00:00 NetworkManager
 5337 ?        00:00:00 NetworkManagerD
 5350 ?        00:00:00 system-tools-ba
 5351 ?        00:00:00 dbus-daemon
 5370 ?        00:00:00 hald
 5371 ?        00:00:00 hald-runner
 5424 ?        00:00:00 sshd
 5448 ?        00:00:00 hald-addon-keyb
 5449 ?        00:00:00 hald-addon-keyb
 5450 ?        00:00:00 hald-addon-keyb
 5457 ?        00:00:00 cupsd
 5459 ?        00:00:00 hald-addon-cpuf
 5460 ?        00:00:00 hald-addon-acpi
 5465 ?        00:00:00 hald-addon-stor
 5546 ?        00:00:00 inetd
 5609 ?        00:00:00 ntpd
 5636 ?        00:00:00 avahi-daemon
 5637 ?        00:00:00 avahi-daemon
 5651 ?        00:00:00 dhcdbd
 5676 ?        00:00:00 hcid
 5688 ?        00:00:00 bluetoothd-serv
 5689 ?        00:00:00 bluetoothd-serv
 5695 ?        00:00:00 krfcommd
 5728 ?        00:00:00 gdm
 5731 ?        00:00:00 gdm
 5734 tty7     00:00:12 Xorg
 5787 ?        00:00:00 dhcpd3
 5797 ?        00:00:00 dhclient
 5847 ?        00:00:00 atd
 5861 ?        00:00:00 cron
 5950 tty7     00:00:00 Xorg
 6058 ?        00:00:00 gnome-keyring-d
 6061 ?        00:00:00 x-session-manag
 6099 ?        00:00:00 ssh-agent
 6102 ?        00:00:00 dbus-launch
 6103 ?        00:00:00 dbus-daemon
 6105 ?        00:00:00 gconfd-2
 6109 ?        00:00:00 gnome-settings-
 6115 ?        00:00:01 metacity
 6117 ?        00:00:02 gnome-panel
 6119 ?        00:00:01 nautilus
 6123 ?        00:00:00 gnome-volume-ma
 6131 ?        00:00:00 bonobo-activati
 6161 ?        00:00:00 gnome-vfs-daemo
 6163 ?        00:00:00 vino-session
 6164 ?        00:00:00 bluetooth-apple
 6171 ?        00:00:00 update-notifier
 6179 ?        00:00:00 evolution-alarm
 6187 ?        00:00:00 nm-applet
 6188 ?        00:00:00 python
 6193 ?        00:00:00 gnome-power-man
 6198 ?        00:00:00 gnome-screensav
 6212 ?        00:00:00 trashapplet
 6224 ?        00:00:00 mapping-daemon
 6249 ?        00:00:00 fast-user-switc
 6251 ?        00:00:00 deskbar-applet
 6253 ?        00:00:00 mixer_applet2
 6454 ?        00:00:00 gksu
 6455 ?        00:00:42 python
 6466 ?        00:00:00 gnome-pty-helpe
[B] 6850 ?        00:00:00 mysqld_safe
12034 ?        00:00:00 mysqld[/B]
12035 ?        00:00:00 logger
12051 ?        00:00:00 notification-da
12053 ?        00:00:00 firefox
12065 ?        00:00:00 run-mozilla.sh
12069 ?        00:00:13 firefox-bin
12087 ?        00:00:00 gnome-terminal
12089 ?        00:00:00 gnome-pty-helpe
12090 pts/0    00:00:00 bash
12107 pts/0    00:00:00 ps
papa@sipper:~$ 

does **this** mean the server is running?

> papa@sipper:~$ sudo dpkg-reconfigure mythtv-database
Failed to connect to database: Access denied for user 'root'@'localhost' (using password: YES) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
It's also possible that mysql-server wasn't running.  After install
is completed, you will need to make sure mysql-server is running
and that you supplied correct information. Try:
sudo dpkg-reconfigure mythtv-database

null root password above

> 
papa@sipper:~$ sudo dpkg-reconfigure mythtv-database
Failed to connect to database: Access denied for user 'root'@'localhost' (using password: YES) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
It's also possible that mysql-server wasn't running.  After install
is completed, you will need to make sure mysql-server is running
and that you supplied correct information. Try:
sudo dpkg-reconfigure mythtv-database
papa@sipper:~$ 

tried the password supplied during the backend install...

no luck

**one more detail.  This is running on edubuntu *server,* not edubuntu**  hope that doesn't matter.

---

### Post by pasta514 on 2007-11-05
Well, I nuked this install and started mythbuntu AMD64 on bare metal.  If I have any issues I can't fix myself I'll let you know.

---

