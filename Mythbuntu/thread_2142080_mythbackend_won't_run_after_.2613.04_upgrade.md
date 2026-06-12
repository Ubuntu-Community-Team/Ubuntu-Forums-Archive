---
title: "mythbackend won't run after .26/13.04 upgrade"
date: 2013-05-04
forum: Mythbuntu
---

### Post by ajaxmike on 2013-05-04
I upgraded to .26 and 13.04.  Dropped mythconverg and recreated an empty  database because there were database errors on the upgrade. I can get into myth-backend setup but mythbackend won't connect to database:
 

**> cat /etc/mythtv/mysql.txt** DBHostName=192.168.1.10 DBUserName=mythtv DBName=mythconverg DBPassword=mythtv **> mythbackend**  Cannot login to database  Would you like to configure the database connection now? [no]   [console is not interactive, using default 'no'] 2013-05-04 14:17:24.067433 C  mythbackend version: fixes/0.26 [v0.26.0-37-g340b5d4] [www.mythtv.org](www.mythtv.org) 2013-05-04 14:17:24.067449 C  Qt version: compile: 4.8.3, runtime: 4.8.4 2013-05-04 14:17:24.067455 N  Enabled verbose msgs:  general 2013-05-04 14:17:24.067462 N  Setting Log Level to LOG_INFO 2013-05-04 14:17:24.067799 I  Added logging to the console 2013-05-04 14:17:24.068212 I  Setup Interrupt handler 2013-05-04 14:17:24.068224 I  Setup Terminated handler 2013-05-04 14:17:24.068231 I  Setup Segmentation fault handler 2013-05-04 14:17:24.068239 I  Setup Aborted handler 2013-05-04 14:17:24.068246 I  Setup Bus error handler 2013-05-04 14:17:24.068255 I  Setup Floating point exception handler 2013-05-04 14:17:24.068265 I  Setup Illegal instruction handler 2013-05-04 14:17:24.068275 I  Setup Real-time signal 0 handler 2013-05-04 14:17:24.068379 N  Using runtime prefix = /usr 2013-05-04 14:17:24.068398 N  Using configuration directory = /root/.mythtv 2013-05-04 14:17:24.068465 I  Assumed character encoding: en_CA.UTF-8 2013-05-04 14:17:24.069084 N  Empty LocalHostName. 2013-05-04 14:17:24.069092 I  Using localhost value of homeserver 2013-05-04 14:17:24.076309 E  Unable to connect to database! 2013-05-04 14:17:24.076326 E  Driver error was [1/1045]: QMYSQL: Unable to connect Database error was: Access denied for user 'mythtv'@'localhost' (using password: YES)  2013-05-04 14:17:24.076418 C  Failed to init MythContext.

---

### Post by BicyclerBoy on 2013-05-04
Appears from that log...the backend is running but can not connect to database.

Beware that there are (/can be) multiple copies of mysql.txt in different locations.

Check the contents of:
$HOME/.mythtv/config.xml
mythtv does not use the .txt file any more..

Find out the running state of these:
sudo service mythtv-backend status
sudo service mysql status
(both these assume upstart jobs which is what mythbuntu uses)

Did you use the database restore script mythconverg_restore.py
[http://www.mythtv.org/wiki/Database_Backup_and_Restore#Replacing_an_existing_database](http://www.mythtv.org/wiki/Database_Backup_and_Restore#Replacing_an_existing_database)

or did you let the installer create a new DB?

If you decide to try the old DB..
There is a database repair/optimize script; can be run from terminal or invoked from mythweb. 

AFAIK The first thing to do after myth upgrade is stop any FE & BE & run mythtv-setup:
stop FE from menus
sudo service mythtv-backend stop
mythtv-setup

You might want to check that mysql has the (required) timezone plugin/extension.

---

### Post by ajaxmike on 2013-05-04
<Configuration>
<Database>
<PingHost>1</PingHost>
<Host>localhost</Host>
<UserName>mythtv</UserName>
<Password>mythtv</Password>
<DatabaseName>mythconverg</DatabaseName>
<Port>3306</Port>
</Database>
<WakeOnLAN>
<Enabled>0</Enabled>
<SQLReconnectWaitTime>0</SQLReconnectWaitTime>
<SQLConnectRetry>5</SQLConnectRetry>
<Command>echo 'WOLsqlServerCommand not set'</Command>
</WakeOnLAN>
<LocalHostName>my-unique-identifier-goes-here</LocalHostName>
</Configuration>

******************

michael@homeserver:~$ sudo service mythtv-backend status
[sudo] password for michael: 
mythtv-backend stop/waiting

michael@homeserver:~$ sudo service mysql status
mysql start/running, process 1363

***************************

I have given up on the old database and trying to create a new one.

*************************

I am confused about the next part.  I ensured that FE and BE were not running.  Then I started mythtv-setup, but that just starts the mythtvbackend and mythfilldatabase.  Then I get the errors above.

Because the .xml file used "localhost" instead of "homserver" or an IP, I changed all of the database permissions to localhost and tried again.  No Joy.

---

### Post by BicyclerBoy on 2013-05-05
mysql start/running, process 1363
- indicates mysql is running

You problem seems to be mythbackend does not connect /does not how to connect to mysql

From your log:
"Using configuration directory = /root/.mythtv"
- implies mythbackend is running as root user, I believe this is a bad, bad idea.

Access denied for user 'mythtv'@'localhost' 

Can you connect to mysql (on local host) with:

echo "select * from recorded ;" | mysql -umythtv -pmythtv mythconverg | head -n 5

If your dB is empty should just get a list of column headings (I think)..

Read thru'  the dB & backend configuration on the mythtv wiki..
When you don't have problems with this stuff you forget the detail.

---

### Post by tgm4883 on 2013-05-05
How did you recreate the database?

---

### Post by billstei on 2013-05-08
Not sure if this will help, but on a number of machines that I have (tried to) set up, I have a normal user account directory, /home/bill, and the MythTV account, /home/mythtv, but I use "bill" to run things like mythtv-setup.  In each of the two home directories is a file config.xml, one having a password of "mythtv" and the other having the actual real password:

/home/bill/.mythtv/config.xml

versus

/home/mythtv/.mythtv/config.xml

the line:

<DBPassword>WHATEVER</DBPassword>

needs to be the correct password (in /home/bill).  You can use a text editor of your choice to fix it.

---

### Post by BicyclerBoy on 2013-05-09
The backend, as started by mythtv-backend upstart job, runs as user "mythtv".
I believe this is the search order:
This looks into
/home/mythtv/.mythtv/config.xml
if it is not found then it uses
/etc/mythtv/config.xml

To ease confusion all possible file locations can be symlinked to one file in
/home/<my-user>/.mythtv/config.xml

The users <my-user> & mythtv must be members of the mythtv group.

The frontend launched from terminal or hot-key etc runs as current user.

You need to note this when debugging scripts that are normally run by backend (mythfilldatabase etc).

---

### Post by RobertSwipe on 2013-05-12
Same problems here after an upgrade from 12.10 to 13.04. The upgrade appeared to fail partway through, although a reboot worked, and the PC does think it's running 13.04.

I've sorted out some of the problems so far, although these may not apply to you.

- MySQL permissions for the "mythtv" database had disappeared. I had to log in as root to mysql (once I'd found my root password!) and run:
 grant all on mythtv.* to mythtv@'localhost';

 You can check if your mysql can see the mythtv database if you log in as the mythtv user:
  mysql --user=mythtv --password=<yourmythtvpassword>
  show databases;

  If this doesn't list the mythtv database (along with any others), you need to grant the permissions as above.

- If I start mythtvbackend from the command line, the front end will work. However, trying to start it as a service fails. The logging process starts OK, but the backend process dies after a few seconds, listing the errors that you have above. It also mentions something about a version mismatch (I'll post some messages later).

I'll keep trying, and report back here if I have any success.

Later:
Well, I've managed to get the backend running as a service. The problem appears to be that the upgrade has clobbered /home/mythtv/.mythtv/config.xml and all the username & password info had been reset to some default values.
Fortunately, the equivalent file existed in my own home folder ~/.mythtv/config.xml and copying the various settings from this file into the clobbered file seems to have borught it all to life.

Now, my only remaining problem (as long as all the recording functions work!) is that the frontend locks up when exiting....

Even later.
Spoke too soon. Backend still working, but mythweb broken. Boo hoo.
Given that my 12.10 installation was a fresh one, this upgrade to 13.04 has been a bit of a disaster. I may well leave other PCs and laptops alone for a while.

Yet more.
My attempts to restore mythweb have reinstalled the mythtv database, so I've lost all details of my recorded stuff.
I tried to reinstall mythplugins - don't do this if you value your database. 
Now, somewhere on my hard drive is a backup of the database, but I don't know where. I guess I'm just going to reinstall the whole thing - including what seems to be a broken 13.04 - and start from scratch.

---

### Post by os2 on 2013-08-03
You need disable Airplay in the frontend for it to stop freezing on exit.


PS. Any luck with running mythbackend as a service?

---

