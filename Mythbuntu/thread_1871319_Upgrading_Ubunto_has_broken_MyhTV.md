---
title: "Upgrading Ubunto has broken MyhTV"
date: 2011-10-28
forum: Mythbuntu
---

### Post by Daminator on 2011-10-28
Hi All,

I 'upgraded' Ubuntu last night. I wish I hadn't, but I did.

I have had the MuthBuntu package installed on top of Ubuntu for a few years now. I've had my share of glitches, but have been very happy for the last couple of years. Hopefully someone can help me get this system back on track.

It's a frontend/backend system I have upgraded.

If I run the frontend, it takes me to country and language and selection screens, then no matter what I do it says "No UPnP" and I have to click 'ok'

The backend setup suffers similarly.

If I run mythbackend from the terminal, I get this:

$ mythbackend
2011-10-28 22:23:57.233 mythbackend version: fixes/0.24 [v0.24.1-99-gfdfc989] [www.mythtv.org](www.mythtv.org)
2011-10-28 22:23:57.234 Using runtime prefix = /usr
2011-10-28 22:23:57.234 Using configuration directory = /home/damian/.mythtv
2011-10-28 22:23:57.234 Empty LocalHostName.
2011-10-28 22:23:57.234 Using localhost value of MythBox
2011-10-28 22:23:57.260 New DB connection, total: 1
2011-10-28 22:23:57.261 Unable to connect to database!
2011-10-28 22:23:57.261 Driver error was [1/2003]:
QMYSQL: Unable to connect
Database error was:
Can't connect to MySQL server on '192.168.0.2' (111)

................................................................................
2011-10-28 22:23:59.311 UPnPautoconf() - No UPnP backends found
2011-10-28 22:23:59.311 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no] 
[console is not interactive, using default 'no']
2011-10-28 22:23:59.312 Deleting UPnP client...
2011-10-28 22:24:00.306 Failed to init MythContext.


Any idea what's going on?

The problem may have been caused by conflicts when I was asked to choose between new versions of files and older versions. Maybe I made the wrong choice at some stage?

Let me know where to go from here if you can.

Once I get myth working again, I'll get to putting Gnome back on. I didn't realise that the latest Ubuntu only had Unity, and seems to have removed Gnome (I can't choose it to log in with).

Thanks for any help
Damian

---

### Post by thatguruguy on 2011-10-28
Type the following in a terminal on your combined fe/be computer, and post the output on this thread:
```
ifconfig
```

---

### Post by Daminator on 2011-10-29
Hi thatguruguy, thanks for replying.

ifconfig returns this:

eth0      Link encap:Ethernet  HWaddr 00:1d:7d:c2:19:a8
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:7dff:fec2:19a8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6525538 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17396633 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:465799029 (465.7 MB)  TX bytes:25047696882 (25.0 GB)
          Interrupt:42 Base address:0x6000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2143 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2143 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1728050 (1.7 MB)  TX bytes:1728050 (1.7 MB)


Is that all in order?

I think the problem may be with mysql .. maybe it's not even running, or maybe it's just not accessible since the upgrade?

I ran:

 sudo netstat -tap | grep mysql

And got nothing returned.

So I ran:

 sudo /etc/init.d/mysql restart

and got:

Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mysql restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) and then start(8) utilities,
e.g. stop mysql ; start mysql. The restart(8) utility is also available.
mysql start/running

So I ran:

 mysql restart

and got:

ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

Then:

 mysql start

and got:

ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)


Does this point to the root of my problem? What's next?

Thanks thatguruguy
Damian

---

### Post by uteck on 2011-10-29
You ned to type:
sudo service mysql start

---

### Post by Daminator on 2011-10-30
Update ..

I have been implementing the advice of everyone who's responding to my from different forums, but still not got things working. Here's the latest:


I ran:

$ sudo start mysql

After a while, I got:

mysql start/running

returned.

I wasn't sure if that meant it had started or if it was telling me the command that I should use, so I tried:

$ sudo mysql start

Which returned:

ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

Then:

$ sudo netstat -tap | grep mysql

Which returned nothing.

Then:

$ sudo service mysql start

Which returned:

start: Job is already running: mysql


So, the message returned form the last command makes me think that mysql is now running, but MythTV still isn't working.

If it's of any help, below is my /etc/mysql/my.cnf file. Do changes need to be made to this since the Ubuntu upgrade? I was advised to cmment out the 'bind-address' section, and I have rebooted since I did that.

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
# [http://dev.mysql.com/doc/mysql/en/server-system-variables.html](http://dev.mysql.com/doc/mysql/en/server-system-variables.html)

# This will be passed to all mysql clients
# It has been reported that passwords should be enclosed with ticks/quotes
# escpecially if they contain "#" chars...
# Remember to edit /etc/mysql/debian.cnf when changing the socket location.
[client]
port        = 3306
socket        = /var/run/mysqld/mysqld.sock

# Here is entries for some specific programs
# The following values assume you have at least 32M ram

# This was formally known as [safe_mysqld]. Both versions are currently parsed.
[mysqld_safe]
socket        = /var/run/mysqld/mysqld.sock
nice        = 0

[mysqld]
#
# * Basic Settings
#

#
# * IMPORTANT
#   If you make changes to these settings and your system uses apparmor, you may
#   also need to also adjust /etc/apparmor.d/usr.sbin.mysqld.
#

user        = mysql
socket        = /var/run/mysqld/mysqld.sock
port        = 3306
basedir        = /usr
datadir        = /var/lib/mysql
tmpdir        = /tmp
skip-external-locking
#
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
# damian, this line seems to be problematic
# damian 2011, was recommended to comment out the line below after ubuntu upgrade problems.
#bind-address        = 127.0.0.1
#
# * Fine Tuning
#
key_buffer        = 16M
max_allowed_packet    = 16M
thread_stack        = 192K
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
query_cache_limit    = 1M
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
#log_slow_queries    = /var/log/mysql/mysql-slow.log
#long_query_time = 2
#log-queries-not-using-indexes
#
# The following can be used as easy to replay backup logs or for replication.
# note: if you are setting up a replication slave, see README.Debian about
#       other settings you may need to change.
#server-id        = 1
#log_bin            = /var/log/mysql/mysql-bin.log
expire_logs_days    = 10
max_binlog_size         = 100M
#binlog_do_db        = include_database_name
#binlog_ignore_db    = include_database_name
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
max_allowed_packet    = 16M

[mysql]
#no-auto-rehash    # faster start of mysql but no tab completition

[isamchk]
key_buffer        = 16M

#
# * IMPORTANT: Additional settings that can override those from this file!
#   The files must end with '.cnf', otherwise they'll be ignored.
#
!includedir /etc/mysql/conf.d/


What should I do next?

Cheers
Damian

---

### Post by newlinux on 2011-11-01
what do:

```
sudo service mysql status
```

and

```
sudo service mythtv-backend status
```

return?

If both say running take a look at your mythtv-backend logs (post relevant content here).

Also make sure you have the proper mysql password and hostname in ~/.mythtv/config.xml

---

### Post by Daminator on 2011-11-01
Hi Newlinux,

Thanks for that. Here's the output of the commands:

$ sudo service mysql status
mysql start/running

$ sudo service mythtv-backend status
mythtv-backend stop/waiting

Does that help at all?

I looked at ~/.mythtv/config.xml the username and password looked like what I expected to see.

what is strange is that I don't seem to be able to log into phpmyadmin.

Upgrading ubuntu doesn't rest any passwords does it?

Damian

---

### Post by newlinux on 2011-11-01
The second command output indicates your backend isn't running. You should try starting your backend and then look at your backend logs in (/var/log/mythtv/ to see why it isn't running. Your earlier posts indicate a problem with connecting to the database. You might want to try connecting manually with the mysql client to make sure your configuration information (username and password) is correct. I'm guessing something is wrong with your login because you can't access it via phpmyadmin either...

to start your backend:

```
 sudo service mythtv-backend start 
```


You may need to reconfigure your DB password.

---

