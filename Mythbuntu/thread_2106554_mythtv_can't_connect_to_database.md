---
title: "mythtv can't connect to database"
date: 2013-01-19
forum: Mythbuntu
---

### Post by kcog on 2013-01-19
Hello,
I know there are solutions out there to this type of problem, like [this one]("http://ubuntuforums.org/showthread.php?t=593832") and [this one]("https://help.ubuntu.com/community/MythTV/Install/Troubleshooting#head-75ded5e7682340f0a88f9ed6ec69a68b6a8b4162").
However none of the suggestions contained therein fixed my problem.

Here's my situation:
I own a HDHR Prime. I'm currently trying to set it up for Clear QAM use, not CableCard.

I have a small net-top Fusion box (Foxconn NT-A3500) with a 64GB SSD, on which I installed Ubuntu minimal (mini.iso) using unetbootin. I then installed the mythbuntu desktop packages. 

I live in northern California, USA, Comcast is my cable (tv & internet) provider 

I had most everything working yesterday.  I hadn't yet tried scheduling recordings, but I could tune all my local channels, the EPG data was populated and working, and I could pause/rwd/ffwd etc. live TV.

The curious thing was this: After all that was working I went into the frontend settings and noticed that the database settings were default and different (e.g. wrong host ip, port, username, password) from what I set up in the initial installation steps and backend setup.  I figured "well it's working so I'll just leave it alone".

I then installed XBMC Frodo RC3, using the automated install/setup script for XBMC in [this thread at the XBMC forums]("http://forum.xbmc.org/showthread.php?tid=141369") (which BTW is pretty awesome and works wonderfully for my hardware).  I then edited GRUB so that the machine booted to XBMC, per [these instructions.]("http://askubuntu.com/questions/148717/how-do-i-boot-into-the-console-and-then-launch-the-ubuntu-desktop-from-it")

Everything was still working fine.  Machine booted to XBMC, and I could CTL-ALT-F2 to a CLI and launch lightdm from there, and still run mythtv functions fine.  XBMC was working well, so I installed the c-myth addon package.  (My intent all along was to use XBMC as the primary frontend for everything)

So in configuring the XBMC c-myth addon frontend settings, I had to supply the database password and username and IP and port.  I tried both the ones I set initially during installation and backend setup, but they didn't work.  I then tried the "default settings" which were the same as the default ones I mentioned above for mythtv frontend, and they didn't work either.  XBMC's myth frontend could not connect to the database.  

So I launched lightdm and went into the myth settings to investigate.

It was at this point that everything was broken.  I can not get mythtv to work at all.  Mythtv-setup can not connect to the database, and I can't seem to edit the mysql username or password.

Can anyone help me troubleshoot this, please?
Thanks! ):P

---

### Post by klc5555 on 2013-01-19
First step: determine if your mysql service is actually running, and accessible by the mythtv user. ```
mysql -u mythtv -p
``` If you can log in and get a mysql prompt, it's running. Exit. Don't know the Ubuntu-random-generated mysql password? There are mysql.txt and/or config.xml files in the /.mythtv directory under the mythtv user, the "you" user, maybe under /etc also. They should have the password (and other data). And of course they should not be zero-byte, nor, if there are more than one copy of each (rather than one copy symlinked everywhere), should their information differ among the copies. 

If attempting to log in to mysql gives you a "can't connect to socket" error, the service is likely not running. ```
sudo netstat -tap | grep mysql
``` may tell you whether the service is running. If it's not, try starting it by hand, with ```
sudo /etc/init.d/mysql start
``` or ```
sudo service mysql start
``` and see if it gets going, or what errors you get [it may direct you to a mysql.err log which will be useful]. If the service starts, and if you can then log into it as above, then you can try starting mythbackend by hand ```
sudo mythbackend
``` which will then either run, or complain, perhaps giving you useful feedback in the terminal window or /var/log/mythtv/mythbackend.log  If the backend starts, try starting mythfrontend (not sudo) from another terminal window. It would be nice is all of this boils down to just an otherwise healthy mysql installation not starting properly at boot. If however, this daisy chain breaks somewhere between mysql starting and mythfrontend starting, check back and maybe we can diagnose it.

But I suppose it could also be that all the supplemental XBMC etc. installing has somehow hosed the mysql configuration a bit. It can be reconfigured...reasonably easily. You'll want first to check the official Ubuntu docs, like this one: [https://help.ubuntu.com/12.04/serverguide/mysql.html](https://help.ubuntu.com/12.04/serverguide/mysql.html)

---

### Post by kcog on 2013-01-19
Thanks.  I will try those steps when I get home tonight.

---

### Post by kcog on 2013-01-19
> **klc5555 said:**
> First step: determine if your mysql service is actually running, and accessible by the mythtv user. ```
mysql -u mythtv -p
``` If you can log in and get a mysql prompt, it's running. Exit. Don't know the Ubuntu-random-generated mysql password? There are mysql.txt and/or config.xml files in the /.mythtv directory under the mythtv user, the "you" user, maybe under /etc also. They should have the password (and other data). And of course they should not be zero-byte, nor, if there are more than one copy of each (rather than one copy symlinked everywhere), should their information differ among the copies. 
Okay, I found a few strange things here.
mysql is running, and I can log in using the default mythtv user and mythtv password.```
xbmc@xbmc:~$ sudo netstat -tap | grep mysql
tcp        0      0 *:mysql                 *:*                     LISTEN      1589/mysqld     
xbmc@xbmc:~$ 

```However, I can not log in using the username (xbmc) and password (****) I supplied when installing the system:
```
xbmc@xbmc:~$ mysql -u xbmc -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'xbmc'@'localhost' (using password: YES)
xbmc@xbmc:~$
```
However, if I look up the mysql.txt files, ```
xbmc@xbmc:~$ sudo find / -name mysql.txt
/home/mythtv/.mythtv/mysql.txt
/etc/mythtv/mysql.txt
xbmc@xbmc:~$ 

```they all contain the port, username xbmc, and the password I supplied during installation.
```
DBPort=6543
DBUserName=xbmc
DBPassword=********
DBName=mythconverg
DBType=QMYSQL

```
Interestingly, the config.xml files contain the same user/password, same IP, but different port:```

NO TWO HOSTS MAY USE THE SAME VALUE
-->
        <DBHostName>192.168.2.12</DBHostName>
        <DBUserName>xbmc</DBUserName>
        <DBPassword>******</DBPassword>
        <DBName>mythconverg</DBName>
        <DBPort>3306</DBPort>

```
Both mysql.txt and config.xml point to /etc/mythtv/ from /home/mythtv/.mythtv/

So I did a find search for config.xml...
```
xbmc@xbmc:~$ sudo find / -name config.xml
[sudo] password for xbmc: 
/home/mythtv/.mythtv/config.xml
/root/.mythtv/config.xml
/usr/share/mythtv/config.xml
/usr/share/doc/mythtv-backend/contrib/config_files/config.xml
/etc/mythtv/config.xml
xbmc@xbmc:~$ 

```
And did a 'cat' view on each of those.  The /root/.mythtv/config.xml one was the same as above (user xbmc, etc.).  But the ones in /usr/share/mythtv/ and 
/usr/share/doc/mythtv-backend/contrib/config_files/config.xml
were not.  They both contained the default username/password of mythtv/mythtv, and the loopback IP and 0 for the port.
```
NO TWO HOSTS MAY USE THE SAME VALUE
-->
        <DBHostName>127.0.0.1</DBHostName>
        <DBUserName>mythtv</DBUserName>
        <DBPassword>mythtv</DBPassword>
        <DBName>mythconverg</DBName>
        <DBPort>0</DBPort>
      </DefaultBackend>

```

So all (two) instances of mysql.txt show user xbmc, same password, same actual IP, same port (6543).  Actually I guess there's really only one instance of mysql.txt, as one of the two points/links to the other.

Of the four (five but one is a link) instances of config.xml, two use the xbmc username, password, and the correct IP, but a different port.  The other two seem to be default files only.

However, I can only login to mysql with the mythtv username. :confused:

I'll review the mysql guide you linked to.  But if you have any further input based on what I've posted here it would be greatly appreciated (again).

One question: if I edit any of these files (mysql.txt or config.xml) will that change anything?  Or do you need to reconfigure/reinstall the database?
Thanks,
KC

EDIT: Well, somehow without changing a thing, I can watch & pause live tv using mythtv frontend again.  However, the discrepancies with the database username, IP, and port still exist.

Most importantly, and probably related, I can not get the XBMC myth frontend addon to talk to the mythtv backend... > "failed to connect to server; Host '192.168.2.12' is blocked because of many connection errors; unblock with 'mysqladmin flush-hosts'"

I tried that command and got this:```
xbmc@xbmc:~/.xbmc/temp$ mysqladmin flush-hosts
mysqladmin: refresh failed; error: 'Access denied; you need (at least one of) the RELOAD privilege(s) for this operation'
xbmc@xbmc:~/.xbmc/temp$ 
```

---

### Post by klc5555 on 2013-01-20
mysqld is running. The original mythbuntu installation set mysql up with the mythtv user as the only mysql user, as its supposed to. My guess is the XBMC installation did not have authorized access to alter the extant mysql installation, and so didn't. The mythtv user owns mysql and the mythconverg database, and XBMC does not, so far as I know, use mysql itself at all, unless one of its addons (like mythbox) independently requires mysql access. So why should the mysql installation be altered for the xbmc account?

Since mysqld is running, confirm whether mythbackend (or mythbackend.real) is running. If it is, it is running using the mythtv login, password, and credentials as it should. If it is not, try to start it in a terminal:```
sudo mythbackend
``` If it starts, great. If not, you'll see errors. If it asks if you want to configure the connection, the mysql information you'll use is the mythtv login and password. Allow it to use its default ports. 

If the backend runs, then the only issue will be to get the frontend(s) connecting properly.

---

### Post by kcog on 2013-01-20
> **klc5555 said:**
> mysqld is running. The original mythbuntu installation set mysql up with the mythtv user as the only mysql user, as its supposed to. My guess is Well, except that I created the mysql user "xbmc" during the original mythbuntu installation.  It was not xbmc that created anything.  I chose that name because this is primarily an XBMC media player box.> the XBMC installation did not have authorized access to alter the extant mysql installation, and so didn't. The mythtv user owns mysql and the mythconverg database, and XBMC does not, so far as I know, use mysql itself at all, unless one of its addons (like mythbox) independently requires mysql access. So why should the mysql installation be altered for the xbmc account?Just for convenience.  I don't mind using the mythtv username, I just liked xbmc better.  It's the main Linux user as well.  Maybe its better to use a different name for that reason though!  :)> 

Since mysqld is running, confirm whether mythbackend (or mythbackend.real) is running.mythbackend runs now only when i manually start it.  It used to start up with the system, now I have to start it from the CLI>  If it is, it is running using the mythtv login, password, and credentials as it should. If it is not, try to start it in a terminal:```
sudo mythbackend
``` If it starts, great. If not, you'll see errors. If it asks if you want to configure the connection, the mysql information you'll use is the mythtv login and password. Allow it to use its default ports. 

If the backend runs, then the only issue will be to get the frontend(s) connecting properly.

Yes, the backend runs.  And the mythtv frontend runs.  But I can not get the XBMC frontend to connect using 'xbmc' credentials, or 'mythtv' user credentials, with either port 3306 or 6543, or either IP 127.0.0.1 or 192.168.2.12 (which is the actual IP of this media box.)  I tried every combination of these with no luck.  Untill....

I was finally able to get the XBMC frontend to talk to the server using the mysql 'root' user and password I set up during installation, 127.0.0.1 IP, and 3306 port.

I'm happy its working, but this is weird, and I don't like using a root user on a regular basis for anything.

Any more suggestions?

Thanks VERY much for your help so far.

---

### Post by klc5555 on 2013-01-20
Well, some progress. Sorta working is much better than not working.

To determine why mythbackend won't start at boot, try restarting it from a CLI, but as a service:```
sudo /etc/init.d/mythtv-backend restart
``` This way mythbackend will write to the mythbackend.log, so if the service fails to start properly, there will be a paper trail. If it's running ```
ps -p `cat /var/run/mythtv/mythbackend.pid`
``` will show it.

If you're trying to set up the xbmc mythbox frontend on the same machine as the backend is running on, trying setting to "localhost" rather than "127.0.0.1" (or "192.168.2.12") for the MySQL database setting in mythbox. It may be that something has gone a bit amiss in the tcpip portion of your mysql setup.

 If "xbmc" really needs to access mysql and mythconverg, this can be easily added. Having logged into mysql as your mysql root user you would (as adapted from the mythtv user manual [http://www.mythtv.org/wiki/User_Manual:Initial_Installation#MythTV_database_setup](http://www.mythtv.org/wiki/User_Manual:Initial_Installation#MythTV_database_setup) ) ```
create user 'xbmc'@'%' identified by 'xbmc';
create user 'xbmc'@'localhost' identified by 'xbmc';
set password for 'xbmc'@'%' = password('[whatever]');
set password for 'xbmc'@'localhost' = password('[whatever]');
connect mythconverg;
grant all privileges on *.* to 'xbmc'@'%' with grant option;
grant all privileges on *.* to 'xbmc'@'localhost' with grant option;
flush privileges;
exit;
```

And restart mysqld

---

### Post by kcog on 2013-01-21
> **klc5555 said:**
> Well, some progress. Sorta working is much better than not working.

To determine why mythbackend won't start at boot, try restarting it from a CLI, but as a service:```
sudo /etc/init.d/mythtv-backend restart
```OK, here's what I get when I try that command:
```
xbmc@xbmc:~$ sudo /etc/init.d/mythtv-backend restart
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service mythtv-backend restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) and then start(8) utilities,
e.g. stop mythtv-backend ; start mythtv-backend. The restart(8) utility is also available.
mythtv-backend start/running, process 2877

```>  This way mythbackend will write to the mythbackend.log, so if the service fails to start properly, there will be a paper trail. If it's running ```
ps -p `cat /var/run/mythtv/mythbackend.pid`
``` will show it.Well apparently it's not running:
```
xbmc@xbmc:~$ ps -p `cat /var/run/mythtv/mythbackend.pid`
cat: /var/run/mythtv/mythbackend.pid: No such file or directory
error: list of process IDs must follow -p

Usage:
 ps [options]

 Try 'ps --help <simple|list|output|threads|misc|all>'
  or 'ps --help <s|l|o|t|m|a>'
 for additional help text.

For more details see ps(1).

``` Although I noticed the output of the first command had a PID assigned, so I tried to check that PID specifically:
```
xbmc@xbmc:~$ ps -p 2877
  PID TTY          TIME CMD
```Nothing.
So based on your comment, I thought I'd check the mythbackend.log file... here are the last several lines of it...
```
Jan 20 22:08:52 xbmc mythbackend[2912]: C thread_unknown mythcommandlineparser.cpp:2534 (ConfigureLogging) mythbackend version: fixes/0.25 [v0.25.2-15-g46cab9         3] www.mythtv.org
Jan 20 22:08:52 xbmc mythbackend[2912]: C thread_unknown mythcommandlineparser.cpp:2536 (ConfigureLogging) Qt version: compile: 4.8.3, runtime: 4.8.3
Jan 20 22:08:52 xbmc mythbackend[2912]: N thread_unknown mythcommandlineparser.cpp:2538 (ConfigureLogging) Enabled verbose msgs:  general
Jan 20 22:08:52 xbmc mythbackend[2912]: N thread_unknown logging.cpp:1176 (logStart) Setting Log Level to LOG_INFO
Jan 20 22:08:52 xbmc mythbackend[2912]: I thread_unknown logging.cpp:229 (FileLogger) Added logging to the console
Jan 20 22:08:52 xbmc mythbackend[2912]: I thread_unknown logging.cpp:369 (SyslogLogger) Added syslogging to facility local7
Jan 20 22:08:52 xbmc mythbackend[2912]: I thread_unknown logging.cpp:425 (DatabaseLogger) Added database logging to table logging
Jan 20 22:08:52 xbmc mythbackend[2912]: N thread_unknown logging.cpp:1215 (logStart) Setting up SIGHUP handler
Jan 20 22:08:52 xbmc mythbackend[2912]: N thread_unknown mythdirs.cpp:51 (InitializeMythDirs) Using runtime prefix = /usr
Jan 20 22:08:52 xbmc mythbackend[2912]: N thread_unknown mythdirs.cpp:64 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Jan 20 22:08:52 xbmc mythbackend[2912]: I CoreContext mythcorecontext.cpp:227 (Init) Assumed character encoding: en_US.UTF-8
Jan 20 22:08:52 xbmc mythbackend[2912]: N CoreContext mythcontext.cpp:477 (LoadDatabaseSettings) Empty LocalHostName.
Jan 20 22:08:52 xbmc mythbackend[2912]: I CoreContext mythcontext.cpp:481 (LoadDatabaseSettings) Using localhost value of xbmc
Jan 20 22:08:52 xbmc mythbackend[2912]: I CoreContext mythcontext.cpp:608 (TestDBconnection) Testing network connectivity to '192.168.2.12'
Jan 20 22:08:52 xbmc mythbackend[2912]: I SystemIOHandlerW system-unix.cpp:90 (run) Starting IO manager (write)
Jan 20 22:08:52 xbmc mythbackend[2912]: I SystemIOHandlerR system-unix.cpp:90 (run) Starting IO manager (read)
Jan 20 22:08:52 xbmc mythbackend[2912]: I SystemSignalManager system-unix.cpp:485 (run) Starting process signal handler
Jan 20 22:08:52 xbmc mythbackend[2912]: I SystemManager system-unix.cpp:263 (run) Starting process manager
Jan 20 22:08:52 xbmc mythbackend[2912]: E CoreContext mythdbcon.cpp:213 (OpenDatabase) Unable to connect to database!
Jan 20 22:08:52 xbmc mythbackend[2912]: E CoreContext mythdbcon.cpp:214 (OpenDatabase) Driver error was [1/2003]:#012QMYSQL: Unable to connect#012Database err         or was:#012Can't connect to MySQL server on '192.168.2.12' (111)
Jan 20 22:08:52 xbmc mythbackend[2912]: A CoreContext mythcontext.cpp:414 (FindDatabase) Cannot login to database?
Jan 20 22:08:52 xbmc mythbackend[2912]: C CoreContext main.cpp:108 (main) Failed to init MythContext.

```However, if I run the command,
```
xbmc@xbmc:~$ mythbackend -d
```Then the backend starts running.  So I'm not sure what to do.
> 
If you're trying to set up the xbmc mythbox frontend(FYI, "mythbox" is the old addon for xbmc, which AFAIK is no longer developed. Not sure if it matters, but there it is. "xbmc-pvr-mythtv-cmyth" is the name of the current supported mythtv frontend addon for xbmc.)> on the same machine as the backend is running on, trying setting to "localhost" rather than "127.0.0.1" (or "192.168.2.12") for the MySQL database setting in mythbox. It may be that something has gone a bit amiss in the tcpip portion of your mysql setup.Well I'd really like to set up the system so that other machines in the house could eventually run frontends too, like a phone or tablet or laptop.
And would this really affect whether the backend starts up when I boot the machine?   Should I still do this given that the backend runs nicely as a daemon with the above command?
> 
 If "xbmc" really needs to access mysql and mythconverg, this can be easily added. Having logged into mysql as your mysql root user you would (as adapted from the mythtv user manual [http://www.mythtv.org/wiki/User_Manual:Initial_Installation#MythTV_database_setup](http://www.mythtv.org/wiki/User_Manual:Initial_Installation#MythTV_database_setup) ) ```
snip code
```And restart mysqldI don't know that user 'xbmc' really needs to access mysql and mythconverg.  I'm okay with using a dedicated user 'mythtv' if that works better.  It might actually avoid some ambiguity I would think...
Is there a reason why 'xbmc' should have access?

---

### Post by klc5555 on 2013-01-21
The backend should not be able to run without root access --it needs to initialize the hardware. So I'm very surprised that ```
mythbackend -d
``` works without sudo.

Was your previously included mythbackend.log information gotten after running```
sudo service mythtv-backend restart
``` as prompted in the terminal's error message? The context directory the service is trying to use according to the log is /home/mythtv/.mythtv while your starting sudo mythbackend -d from a prompt ought to be use /home/xbmc/.mythtv or possibly /root/.mythtv for its configuration information. One of these may have conflicting config.xml or mysql.txt information. Sometimes also config.xml ends up as 0 bytes. 

Also your earlier post mentioned that your manual running of mythbackend -d connected via 127.0.0.1 (or 'localhost') while the service is attempting to use the tcpip socket at 192.168.2.12, implying that the tcpip portion of mysql is not set up quite correctly. Normally this would have been done from the "Services" item in the Mythbuntu Control Center, but the salient features to check will be 1) whether MySQL's  my.cnf file (in Ubuntu normally found under /etc/mysql/ ) has the line "skip-networking" remarked out (#) as it should, and that there is a bind-address line with the correct ip address to listen on (192.168.2.12). And 2) that the .conf file or the script itself used to start MySQL under /etc/init.d does not itself include a SKIP_NETWORKING line or similar, as frequently happens with the MySQL startup scripts/configs in various distros. (I can't remember for certain how Ubuntu does this, I only use the distro for Mythtv frontend machines.) If present, this line too ought to have been remarked out (#). Whereupon the mysql service upon restart ought to be tcpip capable.

---

### Post by kcog on 2013-01-21
> **klc5555 said:**
> The backend should not be able to run without root access --it needs to initialize the hardware. So I'm very surprised that ```
mythbackend -d
``` works without sudo.Well I'm not sure what to say.  I've just copied and pasted everything from my terminal window to these posts, so somehow it works.  > 

Was your previously included mythbackend.log information gotten after running```
sudo service mythtv-backend restart
``` as prompted in the terminal's error message?I pasted the output of that restart command above.  There wasn't really an error message.  I did a 'cat' on the log file just out of curiosity.  But the backend definitely wasn't running yet at that point.  The only time it started running was when i did the 'mythbackend -d' command.>  The context directory the service is trying to use according to the log is /home/mythtv/.mythtv while your starting sudo mythbackend -d from a prompt ought to be use /home/xbmc/.mythtv or possibly /root/.mythtv for its configuration information. One of these may have conflicting config.xml or mysql.txt information. Sometimes also config.xml ends up as 0 bytes. Ugh... makes me want to do a full re-install of the whole system... :(> 
Also your earlier post mentioned that your manual running of mythbackend -d connected via 127.0.0.1 (or 'localhost') while the service is attempting to use the tcpip socket at 192.168.2.12, implying that the tcpip portion of mysql is not set up quite correctly. Normally this would have been done from the "Services" item in the Mythbuntu Control Center, but the salient features to check will be 1) whether MySQL's  my.cnf file (in Ubuntu normally found under /etc/mysql/ ) has the line "skip-networking" remarked out (#) as it should, and that there is a bind-address line with the correct ip address to listen on (192.168.2.12). 
OK, here's the my.cnf file...
```
xbmc@xbmc:~$ cat /etc/mysql/my.cnf
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
port            = 3306
socket          = /var/run/mysqld/mysqld.sock

# Here is entries for some specific programs
# The following values assume you have at least 32M ram

# This was formally known as [safe_mysqld]. Both versions are currently parsed.
[mysqld_safe]
socket          = /var/run/mysqld/mysqld.sock
nice            = 0

[mysqld]
#
# * Basic Settings
#
user            = mysql
pid-file        = /var/run/mysqld/mysqld.pid
socket          = /var/run/mysqld/mysqld.sock
port            = 3306
basedir         = /usr
datadir         = /var/lib/mysql
tmpdir          = /tmp
lc-messages-dir = /usr/share/mysql
skip-external-locking
#
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
bind-address            = 127.0.0.1
#
# * Fine Tuning
#
key_buffer              = 16M
max_allowed_packet      = 16M
thread_stack            = 192K
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
query_cache_limit       = 1M
query_cache_size        = 16M
#
# * Logging and Replication
#
# Both location gets rotated by the cronjob.
# Be aware that this log type is a performance killer.
# As of 5.1 you can enable the log at runtime!
#general_log_file        = /var/log/mysql/mysql.log
#general_log             = 1
#
# Error log - should be very few entries.
#
log_error = /var/log/mysql/error.log
#
# Here you can see queries with especially long duration
#log_slow_queries       = /var/log/mysql/mysql-slow.log
#long_query_time = 2
#log-queries-not-using-indexes
#
# The following can be used as easy to replay backup logs or for replication.
# note: if you are setting up a replication slave, see README.Debian about
#       other settings you may need to change.
#server-id              = 1
#log_bin                        = /var/log/mysql/mysql-bin.log
expire_logs_days        = 10
max_binlog_size         = 100M
#binlog_do_db           = include_database_name
#binlog_ignore_db       = include_database_name
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
max_allowed_packet      = 16M

[mysql]
#no-auto-rehash # faster start of mysql but no tab completition

[isamchk]
key_buffer              = 16M

#
# * IMPORTANT: Additional settings that can override those from this file!
#   The files must end with '.cnf', otherwise they'll be ignored.
#
!includedir /etc/mysql/conf.d/
xbmc@xbmc:~$

``` (btw, is there a way with BB code to put text like that in a smaller box with a vertical scroll bar??  Sorry it's so long.
EDIT: Looks like it defaults to use a scroll bar after some point.  :)

Anyway, that file is strange because it says to listen on port 3306, IP 127.0.0.1, but XBMC can only successfully connect with the backend server if I set port to 6543, 127.0.0.1, and the root mysql user.
> And 2) that the .conf file or the script itself used to start MySQL under /etc/init.d does not itself include a SKIP_NETWORKING line or similar, as frequently happens with the MySQL startup scripts/configs in various distros. (I can't remember for certain how Ubuntu does this, I only use the distro for Mythtv frontend machines.) If present, this line too ought to have been remarked out (#). Whereupon the mysql service upon restart ought to be tcpip capable. I'm not sure I follow you there.  I don't see any .conf or *.conf file in /etc./init.d ... ?

Thanks (again, and still... :) )

---

### Post by klc5555 on 2013-01-21
First off, you'll notice your bind-address in my.cnf has been set to 127.0.0.1, rather than 192.168.2.12. Your MySQL server is therefore only listening to localhost. Anything (like your mythbackend service) that is trying to connect to the ip 192.168.2.12 isn't getting through. You'll want to fix this --edit the bind address to 192.168.2.12. 

After this, restart the mysql service, and you may in fact find mythbackend has now become startable as a service, because the script has been attempting to connect to MySQL on 192.168.2.12. You should also find that your backend and its mysql server can be logged into by Mythfrontends on other machines.

Port 6543/6544 are the ports mythtv runs through. So if you're connecting on these ports, it's a good thing. 3306 on the other hand is MySQL's default port, and should not be accessible from "untrusted hosts". So if you're unable to log into that port, it's also a good thing.

No conf file in /etc/init.d is also OK. Different distros do different things. But also check the launch script itself for mysqld for a SKIP line pertaining to networking. If there's nothing there, then there's nothing to worry about remarking out. My own particular "my.cnf" for MySQL 5.5 still includes a skip-networking line that had to be remmed out, as did my own particular init script. Not having these things is better.

---

### Post by kcog on 2013-01-22
> **klc5555 said:**
> First off, you'll notice your bind-address in my.cnf has been set to 127.0.0.1, rather than 192.168.2.12. Your MySQL server is therefore only listening to localhost. Anything (like your mythbackend service) that is trying to connect to the ip 192.168.2.12 isn't getting through. You'll want to fix this --edit the bind address to 192.168.2.12. 

After this, restart the mysql service, and you may in fact find mythbackend has now become startable as a service, because the script has been attempting to connect to MySQL on 192.168.2.12. You should also find that your backend and its mysql server can be logged into by Mythfrontends on other machines.
OK, I did that.  But it didn't seem to fix anything.  I just  re-booted and the backend is not running.  Still, I have to go to the  CLI and type 'mythbackend -d' (no sudo required).

---

### Post by klc5555 on 2013-01-22
> **kcog said:**
> OK, I did that.  But it didn't seem to fix anything.  I just  re-booted and the backend is not running.  Still, I have to go to the  CLI and type 'mythbackend -d' (no sudo required).

Well this surprising. But anyway...

Has mythtv setup been redone to have the backend use 192.168.2.12 rather than localhost? If you're starting by hand from a terminal, you may also want to use the argument --logfile /var/log/mythtv/mythbackend.log to have it write to the log in this circumstance too. (Though run as user, mythbackend may not have permissions to write to this log. You may have to indicate a path in userspace.)

Is the backend (however started) and the database accessible on 192.168.2.12 rather than localhost by the various frontends? Most importantly, via this supposedly running mythbackend with user credentials, can a signal be got through whatever TV tuner you're using and out Mythfrontend to be viewed? (If not, does it work when the backend is started sudo from a prompt?) If there is (however started) a running backend, a running frontend, and an accessible mythconverg db, all talking through 192.168.2.12 and producing a viewable signal, then we're down to essentially one problem to solve. If the chain is breaking down at some point, then we're back to the logs (backend, frontend, and mysql) to figure out where it's going awry.

---

### Post by kcog on 2013-01-22
> **klc5555 said:**
> Well this surprising. But anyway...

So as I've said I *really* appreciate your help.  This has been great - I feel like I have my own personal tech support guy through this, and I know you post on many other threads, too.  Big Kudos to you.  :D  

But I'm getting discouraged, and I'd like to start fresh and re-do.  My install is fairly young anyway, so there's not much to lose (nothing actually - all my media are on a server, there aren't even any bookmarks saved on this machine) except the time it takes to install, set up and scan channels (which I estimate would only take a few hours all in if I only knew what I was doing).  I feel like it would be faster at this stage to just do it right from the git-go than to chase down what went wrong.  

So with that said, can you recommend a way to get the bare minimum necessary to make a mythtv box with front & back ends on the same box but with the ability to log in from other devices in the future (currently I don't have any other front end hardware, but I want that capability.)

What I did is this:
1) install the Ubuntu mini.iso distro using unetbootin & a USB stick, with absolutely no additional options installed.  Just a bare Ubuntu terminal console, no desktop, nothing (well I did select OpenSSH so I could log in remotely).  I want the most bare, minimalist resource-friendly setup that will run MythTV well.  (honestly it's unfortunate that a GUI desktop is required to run the backend setup, especially since many backends are just servers of sorts... having seen the setup utility there's no reason it couldn't run in a terminal window.)
2) apt-get install [tasksel]("https://help.ubuntu.com/community/Tasksel")
3) using tasksel, install 

[LIST]
[*]mythbuntu-desktop     (Mythbuntu additional roles )
[*]mythbuntu-frontend    (Mythbuntu frontend )
[*]mythbuntu-backend-master      (Mythbuntu master backend )
[*]mythbuntu-backend-slave       (Mythbuntu slave backend)
[/LIST]
5) During the installation (via tasksel) of those task-packages, I'm prompted to fill out several MySQL settings like localhost vs. IP#, root password, etc. (I wonder if this is where things go wrong?)
4) proceed with setup of myth backend, & front end, try to get Myth all set and working (both back and front ends).

Is there a better way (not necessarily easier)? 
Is there an easier way?
Did I miss anything that should be installed?
Should I install something else in place of one of those four things in the list above? (for example, some other desktop, and then just the myth front/back ends)?

In the past, #4 was followed by installation of XBMC, before I had MythTV fully & properly functioning.  This time I would make sure MythTV was working perfectly before messing with anything like XBMC.

The reason why I used the mini.iso install rather than just the mythbuntu.iso, is that I want Ubuntu 12.10 Quantal Quetzal for XBMC reasons, and Mythbuntu is skipping over 12.10 (LTS releases only).

Thanks again.
EDIT: I forgot to mention, that I recently got a CableCard for my HDHomerun (was just running it for Clear QAM unencrypted channels up to now), which will necessitate a new run through the myth setup & channel scan, etc., so I figured I might as well start from scratch anyway.
EDIT2: Maybe this post should be the start of a new thread...?

---

### Post by klc5555 on 2013-01-22
OK, well if you've decided to go new install...

I can't see any advantage to go mini.iso unless you're configuring a backend-only machine. Admittedly Ubuntu has significant bloat and other annoyances associated with it, but Mythbuntu on a machine that is intended to function also as a frontend makes better sense than building it yourself from a mini distro. Certainly vastly easier, and it's been optimized to be a combo backend + frontend. You would simply need to check a box in the Mythbuntu Control Center, and fill in the IP in the backend setup to enable remote frontend connections.

My own setup consists of a network of three backend-only machines and a variety of frontend-only machines that connect to them as necessary. The frontends are on Windows (using Mythtv player), three on Slackware + Mythtv and XBMC, one on Xubuntu + Mythtv, and also an Android tablet + Mythfrontend for Android. The three backends are all on Slackware, where X is only invoked when mythtv-setup needs running, and twm is used as the WM (very minimal and don't need a mouse). Certainly things would be neater for me if there were, say, an ncurses version of the Mythtv backend setup, but it's not like I'm capable of coding the thing.

So in sum, I'd recommend, if your first machine is intended to be entertainment only (rather than a multipurpose desktop), and is intended to be a Mythtv master backend + frontend combo, to which backend other remote frontends are intended to eventually connect, then just go with plain-vanilla Mythbuntu. Get it running as a default localhost, and later change the one setting in the MCC and the ip in the backend and frontend setups to render it remotely connectable. Life is short; save the mini.iso build for when you're putting together the backend-only server sometime in the future.

Just my .02. Go with what's simple, first. Add the complicated stuff later.

---

### Post by kcog on 2013-01-22
The main reason to go with the mini.iso is so I can get MythTV and Ubuntu 12.10.  The script I use to install XBMC simply *nails* all my hardware drivers and settings and saves me a lot of grief and work, but it requires Ubuntu 12.10.

---

### Post by klc5555 on 2013-01-23
> **kcog said:**
> The main reason to go with the mini.iso is so I can get MythTV and Ubuntu 12.10.  The script I use to install XBMC simply *nails* all my hardware drivers and settings and saves me a lot of grief and work, but it requires Ubuntu 12.10.

Of course it does. It wouldn't be Ubuntu if it worked on more than one version :)

OK then. Mythbuntu is mostly a stripped-down Xubuntu, but with its own variant of the XFCE environment, plus extra PVR-related drivers, firmware, tools, and vitamins.

The straightforward way to get what you need on 12.10 would be to install a plain-vanilla Xubuntu. Set the machine up with one user account --your main user. Set it up on static ip. Rip out some of the more obvious things that will be useless for a dedicated PVR, if you wish, like games, graphical e-mail clients, most/all office apps/applets, etc. Install the "mythtv" meta-package and allow it to install to its defaults. It will create the mythtv user and ancillary claptrap. If you use a storage drive for myth recordings, make a mount point for it under the automatically created /var/lib/mythtv/ , mount your drive there, make sure the ownership all the way down to this storage drive and its files is mythtv:mythtv, permissions about 775. Put the mount point properly in fstab. And run the backend setup. When you can watch tv through the standard mythfrontend, like a standard Mythtv machine, then add XBMC, using your script.

Your way with the mini.iso distro should also have worked, and will end up significantly leaner. Clearly your step 5) is where things got off the track. Also, you shouldn't strictly need mythbuntu-desktop (or even XFCE, which certainly is not low-resource any more), just X and a lightweight WM, particularly on a display where XBMC will eventually be the star, not Mythfrontend. If you like editing xinit.rc files (and who doesn't) you might prefer IceWM (which I use a lot on frontends) or possibly even fwvm or fluxbox. And your backend is intended to be a master backend (it will own the database; other machines will connect to it), so "mythbuntu-backend-slave" was also presumably unnecessary.

Finally, the reason I asked whether in your current installation your backend was really running in a usable fashion as you believed (i.e. it could receive TV) when started from the CLI as your regular user without sudo, is that if I were confronted with that circumstance where the backend actually was functional for tuning/watching/recording when run as the normal user, then I would be strongly tempted to simply add ```
xterm -e /usr/bin/mythbackend -d --logfile /[wherever]
``` to my startup apps in the XFCE (or derivative) desktop and call it a night. The way these things usually sort themselves out, after the machine has been running along for a few weeks, inspiration as to how to correct nagging little issues will strike with a slap to the forehead and untangling something like this will end up as an hour project some weekend.

---

