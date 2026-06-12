---
title: "The dread &quot;cannot connect to master backend&quot; error"
date: 2010-12-21
forum: Mythbuntu
---

### Post by Weidbrewer on 2010-12-21
Just had to do a fresh install of everything on my machine for the second time this week (don't ask.)  At this point, I have the MythTV setup down to a science...but this time, it didn't work.  Well, it worked, and then it didn't.

When I first got everything installed with default values, I was able to import my video files, index them, play them, etc.  But, then I needed to set it to be accessed by my three remote frontends.  As such, I changed the Master Backend and Local Backend values to 192.168.1.2 (my network IP for this machine.)  Went to the front and updated the IP there...now it won't connect to the backend.

I have tried subbing in "localhost" into each of those values one at a time (because I'm know I've used that solution before.)  Again, nothing.  In Mythbuntu control center, I tested the MySQL connection, and it checks.  Nothing else has changed from the install defaults at this time, including DB name, MythTV user and MythTV password.  (I intentionally haven't changed anything in regards to MySQL, because I accept that I really don't understand it, and it always ends in tears.)


Any suggestions?


EDIT:  Oops, forgot this part - Ubuntu 64, 10.04.  Myth 23.1 repos installed, current updates as of 10 minutes ago.

---

### Post by ian dobson on 2010-12-22
Hi,

SQL bound to the external IP address on you backend/MySQL server? Have a look in my.cnf for the bind line.

Regards
Ian Dobson

---

### Post by Weidbrewer on 2010-12-22
My.cnf file:

```
#
# The MySQL database server configuration file.
#
# You can copy this to one of:
# - "/etc/mysql/my.cnf" to set global options,
# - "~/.my.cnf" to set user-specific options.
# 
# One can use all long options that the program supports.
# Run program with --help to get a list of available options and with
# --print-defaults to see which it would actually understand and use.
#
# For explanations see
# http://dev.mysql.com/doc/mysql/en/server-system-variables.html

# This will be passed to all mysql clients
# It has been reported that passwords should be enclosed with ticks/quotes
# escpecially if they contain "#" chars...
# Remember to edit /etc/mysql/debian.cnf when changing the socket location.
[client]
port		= 3306
socket		= /var/run/mysqld/mysqld.sock

# Here is entries for some specific programs
# The following values assume you have at least 32M ram

# This was formally known as [safe_mysqld]. Both versions are currently parsed.
[mysqld_safe]
socket		= /var/run/mysqld/mysqld.sock
nice		= 0

[mysqld]
#
# * Basic Settings
#

#
# * IMPORTANT
#   If you make changes to these settings and your system uses apparmor, you may
#   also need to also adjust /etc/apparmor.d/usr.sbin.mysqld.
#

user		= mysql
socket		= /var/run/mysqld/mysqld.sock
port		= 3306
basedir		= /usr
datadir		= /var/lib/mysql
tmpdir		= /tmp
skip-external-locking
#
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
bind-address		= 127.0.0.1
#
# * Fine Tuning
#
key_buffer		= 16M
max_allowed_packet	= 16M
thread_stack		= 192K
thread_cache_size       = 8
# This replaces the startup script and checks MyISAM tables if needed
# the first time they are touched
myisam-recover         = BACKUP
#max_connections        = 100
#table_cache            = 64
#thread_concurrency     = 10
#
# * Query Cache Configuration
#
query_cache_limit	= 1M
query_cache_size        = 16M
#
# * Logging and Replication
#
# Both location gets rotated by the cronjob.
# Be aware that this log type is a performance killer.
# As of 5.1 you can enable the log at runtime!
#general_log_file        = /var/log/mysql/mysql.log
#general_log             = 1

log_error                = /var/log/mysql/error.log

# Here you can see queries with especially long duration
#log_slow_queries	= /var/log/mysql/mysql-slow.log
#long_query_time = 2
#log-queries-not-using-indexes
#
# The following can be used as easy to replay backup logs or for replication.
# note: if you are setting up a replication slave, see README.Debian about
#       other settings you may need to change.
#server-id		= 1
#log_bin			= /var/log/mysql/mysql-bin.log
expire_logs_days	= 10
max_binlog_size         = 100M
#binlog_do_db		= include_database_name
#binlog_ignore_db	= include_database_name
#
# * InnoDB
#
# InnoDB is enabled by default with a 10MB datafile in /var/lib/mysql/.
# Read the manual for more InnoDB related options. There are many!
#
# * Security Features
#
# Read the manual, too, if you want chroot!
# chroot = /var/lib/mysql/
#
# For generating SSL certificates I recommend the OpenSSL GUI "tinyca".
#
# ssl-ca=/etc/mysql/cacert.pem
# ssl-cert=/etc/mysql/server-cert.pem
# ssl-key=/etc/mysql/server-key.pem



[mysqldump]
quick
quote-names
max_allowed_packet	= 16M

[mysql]
#no-auto-rehash	# faster start of mysql but no tab completition

[isamchk]
key_buffer		= 16M

#
# * IMPORTANT: Additional settings that can override those from this file!
#   The files must end with '.cnf', otherwise they'll be ignored.
#
!includedir /etc/mysql/conf.d/
```

---

### Post by newlinux on 2010-12-22
```

# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
bind-address		= 127.0.0.1

```

Is most likely the offender. Comment out that bind-address line, restart mysql and try again.

---

### Post by Weidbrewer on 2010-12-22
> **newlinux said:**
> ```

# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
bind-address		= 127.0.0.1

```

Is most likely the offender. Comment out that bind-address line, restart mysql and try again.

Thanks!  I'll give that a whack when I get home and see what happens.  (Also, please refresh my memory - what's the command to restart MySQL, again?  I was googling that the other day for something, and the syntax I'd found errored out and I got sidetracked.)

Any idea how this error slipped in on this install?  Like I said, didn't happen with an install I did two days ago on the same machine...

---

### Post by newlinux on 2010-12-22
> **Weidbrewer said:**
> Thanks!  I'll give that a whack when I get home and see what happens.  (Also, please refresh my memory - what's the command to restart MySQL, again?  I was googling that the other day for something, and the syntax I'd found errored out and I got sidetracked.)


```

sudo service mysql restart

```

should do the trick.
> 
Any idea how this error slipped in on this install?  Like I said, didn't happen with an install I did two days ago on the same machine...

I've never actually installed mythbuntu formally. I've always installed mythtv on top of a regular ubuntu install, but maybe there is a question that gets asked that configures mysql for remote access. I believe in the mythbuntu-control-centre mysql section there is an option for that under master backend role - can check for sure later...

---

### Post by Weidbrewer on 2010-12-22
> **newlinux said:**
> ```

sudo service mysql restart

```

should do the trick.


Thanks

> 
I've never actually installed mythbuntu formally.


I generally do, just because that's the disk I have on hand most of the time...  :)

> 
but maybe there is a question that gets asked that configures mysql for remote access. I believe in the mythbuntu-control-centre mysql section there is an option for that under master backend role - can check for sure later...

There is and there is.  I configured it in setup for remote access and then went and double-checked in the Control Center to be sure.  Strange...

But, yup - I configure anything they give me options for in setup, but I love the control center and generally trust that to not steer me wrong and have the final say.

---

### Post by Weidbrewer on 2010-12-22
Nope...still doesn't work.   Currently, I have 192.168.1.2 set for all thee values (Master, local and frontend) though I did try subbing in localhost for each to see what happened.  also, in case the restart command didn't work, I rebooted the machine.

What next?


EDIT:  Okay...just did a reinstall.  Haven't finished installing everything or testing frontends yet, but so far, so good.  IP is correct everywhere it needs to be on the combo backend/frontend.

---

### Post by Weidbrewer on 2010-12-22
Everything installed but Gnome desktop, which should have no effect on this.  Everything works on the combo backend - files are there, Myth starts and i can watch stuff.

Booted up a remote frontend, and it "found" the backend, in that it populated the IP address and password automatically...but won't connect.  Keeps giving me the "cannot login" warning.  Checking the Control Center on that frontend, it fails the "test connection" option under the MySQL tab.  (My hatred for MySQL knows no bounds.)

---

### Post by Weidbrewer on 2010-12-26
Anyone have any ideas?

---

### Post by ian dobson on 2010-12-26
Hi,

Sounds as if the password on the frontend is incorrect. Have a look in your mysql.txt file on the backend and frontend.

Regards
Ian Dobson

---

### Post by Weidbrewer on 2010-12-26
Sorry for not being clear.  What I meant above about the password is that I have the same password for mythconverg, user mythtv in the remote front end setup as I have on the local front end on the primary back end.  The ip address is also entered correctly.  Furthermore, it found the back end, as all of this info was populated automatically on first boot of the remote front end (although I still verified it.). Even given that all of this is correct, it will not connect.  Also, Mythbuntu control center says that it is not connecting to the DB.

Is there a different password that you are referring to? (none others that I have ever needed before...)

Thank you for taking the time to help out!

---

### Post by newlinux on 2010-12-26
It is still worth checking your mysql.txt files and config.xml files to make sure they have the right IP address and passwords and user as well.

---

### Post by Weidbrewer on 2010-12-26
Here is my mysql.txt:

```
DBHostName=localhost

# By default, Myth tries to ping the DB host to see if it exists.
# If your DB host or network doesn't accept pings, set this to no:
#
#DBHostPing=no

DBUserName=mythtv
DBName=mythconverg
DBType=QMYSQL3

# Set the following if you want to use something other than this
# machine's real hostname for identifying settings in the database.
# This is useful if your hostname changes often, as otherwise you
# will need to reconfigure mythtv every time.
# NO TWO HOSTS MAY USE THE SAME VALUE
#
#LocalHostName=my-unique-identifier-goes-here

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
DBPassword=**{correct password is here}**
```

And the config.xml:

```
<Configuration>
&#8722;
<UPnP>
&#8722;
<MythFrontend>
&#8722;
<DefaultBackend>
&#8722;
<!--

Set the <LocalHostName> hostname override below only if you want to use
something other than the machine's real hostname for identifying settings
in the database.  This is useful if your hostname changes often, as
otherwise you'll need to reconfigure mythtv every time.

NO TWO HOSTS MAY USE THE SAME VALUE
-->
<DBHostName>localhost</DBHostName>
<DBUserName>mythtv</DBUserName>
<DBPassword>**{correct password is here}**</DBPassword>
<DBName>mythconverg</DBName>
<DBPort>0</DBPort>
</DefaultBackend>
</MythFrontend>
</UPnP>
</Configuration>
```


If anything needs to be changed, I would request some background on it - I really like to know *why* I'm changing something, not just fixing it (teach a man to fish, and all that...)  Also, I'm hyper paranoid, as right now the backend is working, and I'm scared of screwing it up through not fully understanding something I'm told to do...

Thanks again!

---

### Post by ian dobson on 2010-12-26
> **Weidbrewer said:**
> Here is my mysql.txt:

```
DBHostName=localhost

# By default, Myth tries to ping the DB host to see if it exists.
# If your DB host or network doesn't accept pings, set this to no:
#
#DBHostPing=no

DBUserName=mythtv
DBName=mythconverg
DBType=QMYSQL3

# Set the following if you want to use something other than this
# machine's real hostname for identifying settings in the database.
# This is useful if your hostname changes often, as otherwise you
# will need to reconfigure mythtv every time.
# NO TWO HOSTS MAY USE THE SAME VALUE
#
#LocalHostName=my-unique-identifier-goes-here

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
DBPassword=**{correct password is here}**
```

And the config.xml:

```
<Configuration>
&#8722;
<UPnP>
&#8722;
<MythFrontend>
&#8722;
<DefaultBackend>
&#8722;
<!--

Set the <LocalHostName> hostname override below only if you want to use
something other than the machine's real hostname for identifying settings
in the database.  This is useful if your hostname changes often, as
otherwise you'll need to reconfigure mythtv every time.

NO TWO HOSTS MAY USE THE SAME VALUE
-->
<DBHostName>localhost</DBHostName>
<DBUserName>mythtv</DBUserName>
<DBPassword>**{correct password is here}**</DBPassword>
<DBName>mythconverg</DBName>
<DBPort>0</DBPort>
</DefaultBackend>
</MythFrontend>
</UPnP>
</Configuration>
```


If anything needs to be changed, I would request some background on it - I really like to know *why* I'm changing something, not just fixing it (teach a man to fish, and all that...)  Also, I'm hyper paranoid, as right now the backend is working, and I'm scared of screwing it up through not fully understanding something I'm told to do...

Thanks again!

Is that from your backend? The DBHostName is localhost which is wrong for the remote frontend.

Regards
Ian Dobson

---

### Post by Weidbrewer on 2010-12-26
> **ian dobson said:**
> Is that from your backend? The DBHostName is localhost which is wrong for the remote frontend.

Regards
Ian Dobson

Yessir, that is from the backend.  Only place I would have thought to look.  Not being flip, just stating a fact, but I have never had to do anything with either of those files on a remote frontend (and I currently have three remote frontends that were working fine until this install.)  Now, granted, it is *fully *possible with my luck that Myth changed something in an update between the fresh install I did on the backend Sunday and the one that I did Monday or Tuesday, but that would make me a bit miffed.

On the frontend, in setup, I have the IP of the backend (192.168.1.2) listed, with the above user, DB and password.  (again, populated automatically the first time that I booted it, as usual.)  Never had to do anything differently on the frontends.  Just boot up, double check the info, and log in.

---

### Post by newlinux on 2010-12-26
> **Weidbrewer said:**
> Yessir, that is from the backend.  Only place I would have thought to look.  Not being flip, just stating a fact, but I have never had to do anything with either of those files on a remote frontend (and I currently have three remote frontends that were working fine until this install.)  Now, granted, it is *fully *possible with my luck that Myth changed something in an update between the fresh install I did on the backend Sunday and the one that I did Monday or Tuesday, but that would make me a bit miffed.

On the frontend, in setup, I have the IP of the backend (192.168.1.2) listed, with the above user, DB and password.  (again, populated automatically the first time that I booted it, as usual.)  Never had to do anything differently on the frontends.  Just boot up, double check the info, and log in.

I meant you should check the files on the frontend that isn't connecting properly. I've seen it more than a handful of times where these files are wrong. And there are multiple mysql.txt files (/etc/mythtv/mysql.txt, ~/.mythtv/mysql.txt, /home/mythtv/mysql.txt - but you may have these symlinked). If you want to be thorough despite the fact that it doesn't make sense or you've never had to to do it is still worth checking as it takes very little time to do so. It has been a problem before. the fast that it is not behaving as it has before or as expected lends itself to you looking places you haven't before. Other than that, start examining your front and backend logfiles fot clues. Usually, those are the first places you want to look for clues, and may require turning up the verbosity of the logs.

---

### Post by newlinux on 2010-12-26
Also, make sure your masterbackend is set to use it's IP address, and not localhost or the local IP address. It needs to be an externally accessible IP in your master backend setup (mythtv-setup). I know you said before you subbed in localhost - just making sure you changed it back.

---

### Post by Weidbrewer on 2010-12-26
> **newlinux said:**
> If you want to be thorough despite the fact that it doesn't make sense or you've never had to to do it is still worth checking as it takes very little time to do so. 

I get that, which is why I was trying to make it very clear I wasn't being a smartass - just trying to ensure that we're all talking about the same thing.

Yes, both IP address locations in the setup on the backend have "192.168.1.2" listed in them instead of "localhost."

Checked the two files on the frontend and:

mysql.txt:

```
DBHostName=192.168.1.2

# By default, Myth tries to ping the DB host to see if it exists.
# If your DB host or network doesn't accept pings, set this to no:
#
#DBHostPing=no

DBUserName=mythtv
DBPassword=**{correct password}**
DBName=mythconverg
DBType=QMYSQL3

# Set the following if you want to use something other than this
# machine's real hostname for identifying settings in the database.
# This is useful if your hostname changes often, as otherwise you
# will need to reconfigure mythtv every time.
# NO TWO HOSTS MAY USE THE SAME VALUE
#
#LocalHostName=my-unique-identifier-goes-here

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

config.xml:
```
<Configuration>
  <UPnP>
    <UDN>
      <MediaRenderer>55f2a1f0-7af8-4ec8-b631-5b6c8b3a131a</MediaRenderer>
    </UDN>
    <MythFrontend>
      <DefaultBackend>
        <USN/>
        <SecurityPin>0000</SecurityPin>
        <DBHostName>192.168.1.2</DBHostName>
        <DBUserName>mythtv</DBUserName>
        <DBPassword>**{wrong password, waddya know?}**</DBPassword>
        <DBName>mythconverg</DBName>
        <DBPort>0</DBPort>
      </DefaultBackend>
    </MythFrontend>
  </UPnP>
</Configuration>
```

So...I opened the file in gedit and changed the password, then saved it.  Opened Myth, and it still cannot connect.

---

### Post by Weidbrewer on 2010-12-26
> **newlinux said:**
> Also, make sure your masterbackend is set to use it's IP address, and not localhost or the local IP address. It needs to be an externally accessible IP in your master backend setup (mythtv-setup). I know you said before you subbed in localhost - just making sure you changed it back.

Additional on this front - again, only because I want to make sure that I'm understanding something that hasn't been required before - When you say "Externally accessible," you don't mean "external from outside my network," do you?  As in, something like, 96.xxx.xx.xxx?  I've never used anything except my local in-network IP before.

EDIT:  Also tried a different frontend - same error in the .xml file, edited the same way, also cannot connect.

---

### Post by newlinux on 2010-12-26
> **Weidbrewer said:**
> Additional on this front - again, only because I want to make sure that I'm understanding something that hasn't been required before - When you say "Externally accessible," you don't mean "external from outside my network," do you?  As in, something like, 96.xxx.xx.xxx?  I've never used anything except my local in-network IP before.

EDIT:  Also tried a different frontend - same error in the .xml file, edited the same way, also cannot connect.

[http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Backend#Host_Address_Backend_Setup](http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Backend#Host_Address_Backend_Setup)

No I mean frontends external to your master backend machine on your network. If your master backend  (not frontend config files, but backend setup) defines it IP address as localhost other machines won't be able to connect to it. By local IP address  (not to use) i meant loopback, or 127.0.0.1, if that's what confused you. I'm not sure what you mean by this hasn't been required before.


Nothing you can do from myth will make it accessible to external networks if you are on a somewhat typical home network. That will be controlled by your router and firewall.

Again, the next (first) place to look is your logs...

---

### Post by Weidbrewer on 2010-12-26
Yes, that is what I thought you meant by external, but wanted to make sure.

As for logs, front end, back end or both?  Also, what is the best way to go about getting the verbose logs that were mentioned earlier?

---

### Post by newlinux on 2010-12-26
In this case I'd start off with the frontend logs from when its not connecting.

you can get the verbosity for the frontend by doing:
```

mythfrontend -v help

```

In this case since it seems to not be connecting to the database I might recommend

```

mythfrontend -v database -l /var/log/mythtv/mythfrontend.log

```

(or you can log them to the screen or another log location)

you may just want to start off by looking at your existing logs from when it hasn't connected in both your front and backend.

---

### Post by Weidbrewer on 2010-12-26
Per your request:

```
2010-12-26 22:09:27.727 mythfrontend version: branches/release-0-23-fixes [26863] www.mythtv.org
2010-12-26 22:09:27.727 Using runtime prefix = /usr
2010-12-26 22:09:27.727 Using configuration directory = /home/*******/.mythtv
2010-12-26 22:09:28.417 Empty LocalHostName.
2010-12-26 22:09:28.417 Using localhost value of {FRONTEND}
2010-12-26 22:09:28.417 Clearing Settings Cache.
2010-12-26 22:09:28.417 Testing network connectivity to '192.168.1.2'
2010-12-26 22:09:28.423 Clearing Settings Cache.
2010-12-26 22:09:28.429 New DB connection, total: 1
2010-12-26 22:09:28.430 Unable to connect to database!
2010-12-26 22:09:28.430 Driver error was [1/2003]:
QMYSQL: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.1.2' (111)


2010-12-26 22:09:28.606 UPnPautoconf() - Found one UPnP backend
2010-12-26 22:09:28.686 Testing network connectivity to '192.168.1.2'
2010-12-26 22:09:28.691 Closing DB connection named 'DBManager0'
2010-12-26 22:09:28.691 Clearing Settings Cache.
2010-12-26 22:09:28.692 Unable to connect to database!
2010-12-26 22:09:28.692 Driver error was [1/2003]:
QMYSQL: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.1.2' (111)

2010-12-26 22:09:28.692 Cannot login to database?
2010-12-26 22:09:28.693 Primary screen: 0.
2010-12-26 22:09:28.693 Using screen 0, 640x480 at 0,0
2010-12-26 22:09:28.694 Could not find theme:  - Switching to Terra
2010-12-26 22:09:28.694 Using theme base resolution of 1280x720
2010-12-26 22:09:28.703 Desktop video mode: 640x480 120.005 Hz
2010-12-26 22:09:28.712 get_ip: Name or service not known
2010-12-26 22:09:28.712 LIRC, Error: Failed to parse IP address ''
2010-12-26 22:09:28.712 JoystickMenuThread Error: Joystick disabled - Failed to read /home/*******/.mythtv/joystickmenurc
2010-12-26 22:09:28.725 Using Frameless Window
2010-12-26 22:09:28.725 Using Full Screen Window
2010-12-26 22:09:28.728 Using the Qt painter
2010-12-26 22:09:33.652 Writing settings file /home/*******/.mythtv/mysql.txt
2010-12-26 22:09:33.653 Closing DB connection named 'DBManager0'
2010-12-26 22:09:33.653 Clearing Settings Cache.
2010-12-26 22:09:33.662 Testing network connectivity to '192.168.1.2'
2010-12-26 22:09:33.673 Closing DB connection named 'DBManager0'
2010-12-26 22:09:33.673 Clearing Settings Cache.
2010-12-26 22:09:33.674 Unable to connect to database!
2010-12-26 22:09:33.674 Driver error was [1/2003]:
QMYSQL: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.1.2' (111)

2010-12-26 22:09:33.674 Cannot login to database?
2010-12-26 22:09:33.674 Cannot login to database?
2010-12-26 22:09:33.674 Clearing Cache of overridden 'theme' ignored.
2010-12-26 22:09:33.687 Primary screen: 0.
2010-12-26 22:09:33.688 Using screen 0, 640x480 at 0,0
2010-12-26 22:09:33.688 Using theme base resolution of 1280x720
2010-12-26 22:09:33.689 get_ip: Name or service not known
2010-12-26 22:09:33.689 LIRC, Error: Failed to parse IP address ''
2010-12-26 22:09:33.689 JoystickMenuThread Error: Joystick disabled - Failed to read /home/*******/.mythtv/joystickmenurc
2010-12-26 22:09:33.702 Using Frameless Window
2010-12-26 22:09:33.702 Using Full Screen Window
2010-12-26 22:09:33.703 Using the Qt painter
2010-12-26 22:09:36.243 User cancelled database configuration
2010-12-26 22:09:36.256 Failed to init MythContext, exiting.
2010-12-26 22:09:36.256 Deleting UPnP client...
```

I redacted some info for privacy, but one thing that I noticed was this part: ```
2010-12-26 22:09:28.417 Using localhost value of {FRONTEND}
``` where "{FRONTEND} is the network name of my remote frontend.  Not sure if this means anything, but it stood out to me.

Also, it says ```
mythfrontend version: branches/release-0-23-fixes
``` but I am using 0.23.1...again, not sure if it is important, but there it is.

---

### Post by Weidbrewer on 2010-12-28
*sigh*  Okay...I seem to have stumped the masses and have been without my media server my whole holiday vacation from work (when I would have really liked to have it.)  I'm done fighting with it.  I'm gonna throw in the towel and reinstall the OS when I get home...again...  (This time, I'll try the route of vanilla Ubuntu 10.04 then installing Myth over it.)

If this doesn't work, I'm probably going to have to just explore other options.

---

### Post by Weidbrewer on 2010-12-28
The third time, she is the charm.

Installed the standard Ubuntu, then MCC and now everything works as it should.

Give that the install this way covered a few important options - such as setting a root MySQL password - I'm really thinking the Mythbuntu ISO is missing some key features and won't be using it again.

Even though we weren't able to fix the problem - I'm good at finding those - I thank everyone for giving it a shot.

---

