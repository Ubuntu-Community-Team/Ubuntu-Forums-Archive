---
title: "[SOLVED] Cannot Login to Database - Ultimate 1.9"
date: 2008-09-22
forum: Mythbuntu
---

### Post by Buschbarber on 2008-09-22
I am running Ultimate 1.9 on an HP MCE M7060n P4, 3Ghz, 2Gb ram, WinTV HVR 1600, Nvidia 6200OC video card. I followed the instructions, from the MythTV website, to install MythTV. After the install, I ran the MythTV Backend Setup, and it quits with the message Failed to Login to Database. I am not using a password for the database, per the suggestions in the Install instructions.

What can I do, next?

---

### Post by OffAxis on 2008-09-22
you can check your ~.mythtv/mysql.txt file and see if your name and password are listed there. If not, try this:

[http://www.debian-administration.org/articles/442](http://www.debian-administration.org/articles/442)
(I'm not sure which version that's for)

Here's the official docs:
[http://dev.mysql.com/doc/refman/5.0/en/resetting-permissions.html](http://dev.mysql.com/doc/refman/5.0/en/resetting-permissions.html)

---

### Post by Buschbarber on 2008-09-22
Here are the contents of the mythsql.txt file. It still will not 

DBHostName=rich-desktop

# By default, Myth tries to ping the DB host to see if it exists.
# If your DB host or network doesn't accept pings, set this to no:
#
DBHostPing=no

DBUserName=mythtv
DBPassword=
DBName=mythconverg
DBType=QMYSQL3

# Set the following if you want to use something other than this
# machine's real hostname for identifying settings in the database.
# This is useful if your hostname changes often, as otherwise you
# will need to reconfigure mythtv (or futz with the DB) every time.
# TWO HOSTS MUST NOT USE THE SAME VALUE
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

Whether or not I run the Frontend or Backend Setup, it still refuses to allow me to Login to the DB. I am not using a password, per the instructions.

---

### Post by Buschbarber on 2008-09-22
I went to the first link you posted and tried to change the password for the DB

I used my Root password and I received this error

rich@rich-desktop:~$ mysql --user=root --pass mysql
Enter password: 
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
rich@rich-desktop:~$

---

### Post by Buschbarber on 2008-09-22
Following the instructions, I tried to stop the DB and I received this error

rich@rich-desktop:~$ /etc/init.d/mysql stop
open: Permission denied
 * Stopping MySQL database server mysqld                                        open: Permission denied
                                                                         [ OK ]
rich@rich-desktop:~$

---

### Post by volkswagner on 2008-09-23
> **Buschbarber said:**
> Following the instructions, I tried to stop the DB and I received this error

rich@rich-desktop:~$ /etc/init.d/mysql stop
open: Permission denied
 * Stopping MySQL database server mysqld                                        open: Permission denied
                                                                         [ OK ]
rich@rich-desktop:~$

You need root privileges to start/stop/restart services.
```

sudo /etc/init.d/mysql stop
```

I have seen where installing mythtv on top of an existing desktop, mysql fails to install or create the database.

You may need to verify it is installed.

---

### Post by Buschbarber on 2008-09-23
Can you tell me the steps to verify that MySQL has been installed? I am new to Linux. Also, do you know why I am getting the message 

rich@rich-desktop:~$ mysql --user=root --pass mysql
Enter password:
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
rich@rich-desktop:~$

---

### Post by volkswagner on 2008-09-23
> **Buschbarber said:**
> Can you tell me the steps to verify that MySQL has been installed? I am new to Linux. Also, do you know why I am getting the message 

rich@rich-desktop:~$ mysql --user=root --pass mysql
Enter password:
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
rich@rich-desktop:~$

Please post the output of the following.

```
dpkg --get-selections mysql*
```

---

### Post by Buschbarber on 2008-09-23
rich@rich-desktop:~$ dpkg --get-selections mysql*
mysql-client					install
mysql-client-5.0				install
mysql-common					install
mysql-gui-tools-common				install
mysql-server					install
mysql-server-5.0				install
rich@rich-desktop:~$

---

### Post by volkswagner on 2008-09-23
That looks good.  What do you get when you try to restart mysql?  Any errors?
```

sudo /etc/init.d/mysqld restart
```

Also check mysql logs, /var/log/mysql.log and /var/log/mysql.err

You may need to run the following.  

```
sudo dpkg-reconfigure mysql-server
```

---

### Post by Buschbarber on 2008-09-23
rich@rich-desktop:~$ sudo /etc/init.d/mysqld restart
[sudo] password for rich: 
sudo: /etc/init.d/mysqld: command not found
rich@rich-desktop:~$ sudo /etc/init.d/mysqld restart
sudo: /etc/init.d/mysqld: command not found
rich@rich-desktop:~$ 

Both logs are blank

rich@rich-desktop:~$ sudo /etc/init.d/mysqld restart
[sudo] password for rich: 
sudo: /etc/init.d/mysqld: command not found
rich@rich-desktop:~$ sudo /etc/init.d/mysqld restart
sudo: /etc/init.d/mysqld: command not found
rich@rich-desktop:~$ sudo dpkg-reconfigure mysql-server
rich@rich-desktop:~$ 

I have attached a screenprint of the screen I see when I try to run the Backend Setup and it ends with Cannot Login to Database. Then it asks if I want to run the database configurator. I type in Y and hit enter and the attached screen is what I see.

---

### Post by atchase on 2008-09-24
I was having the same problem and found the answer here toward the bottom of the page.

[http://ph.ubuntuforums.com/showthread.php?t=790814](http://ph.ubuntuforums.com/showthread.php?t=790814)


I ran  sudo dpkg-reconfigure mythtv-database   like it said to and that command rebuilt the SQL Database and I logged right in.
Hope it helps.

Aaron

---

### Post by Buschbarber on 2008-09-24
I have run that command but it came back with an error

rich@rich-desktop:~$ sudo dpkg-reconfigure mythtv-database
Failed to connect to database: Can't connect to MySQL server on 'rich-desktop' (111) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
It's also possible that mysql-server wasn't running.  After install
is completed, you will need to make sure mysql-server is running
and that you supplied correct information. Try:
sudo dpkg-reconfigure mythtv-database
rich@rich-desktop:~$

---

### Post by volkswagner on 2008-09-24
Sorry for the error, the mysql start/stop/restart.

Should be

```
sudo /etc/init.d/mysql restart
```

Check to see mysql is listed in /etc/init.d and is executable.

```
ls -alt /etc/init.d
```

Mine looks like this

-rwxr-xr-x  1 root root 5815 2007-12-20 16:38 mysql

Did you ever set a mysql root password?  According to the following post, a blank password did not work.  Poster was getting the same error as you.

[http://ubuntuforums.org/showthread.php?t=639161&page=2]("http://ubuntuforums.org/showthread.php?t=639161&page=2")

---

### Post by Buschbarber on 2008-09-24
rich@rich-desktop:~$ sudo /etc/init.d/mysql restart
[sudo] password for rich: 
 * Stopping MySQL database server mysqld                                 [ OK ] 
 * Starting MySQL database server mysqld                                 [ OK ] 
 * Checking for corrupt, not cleanly closed and upgrade needing tables.
rich@rich-desktop:~$ ls -alt /etc/init.d
total 496
drwxr-xr-x 158 root root 12288 2008-09-24 01:42 ..
drwxr-xr-x   2 root root  4096 2008-09-22 00:15 .
-rwxr-xr-x   1 root root  1084 2008-08-01 09:43 anacron
-rwxr-xr-x   1 root root  7053 2008-07-25 03:23 ufw
-rwxr-xr-x   1 root root  6312 2008-07-25 02:36 kdm
-rwxr-xr-x   1 root root  1224 2008-07-25 02:33 winbind
-rwxr-xr-x   1 root root  2301 2008-07-22 11:58 hal
-rwxr-xr-x   1 root root  6257 2008-07-18 11:20 clamav-freshclam
-rwxr-xr-x   1 root root  3134 2008-07-17 15:12 gdm
-rwxr-xr-x   1 root root   349 2008-07-10 19:05 linux-restricted-modules-common
-rwxr-xr-x   1 root root  1187 2008-06-05 16:03 kde-guidance
-rwxr-xr-x   1 root root  2500 2008-06-03 06:57 mythtv-backend
-rwxr-xr-x   1 root root  3334 2008-05-27 15:33 casper
-rwxr-xr-x   1 root root  2181 2008-05-17 06:54 apport
-rwxr-xr-x   1 root root  4546 2008-05-14 21:43 dbus
-rwxr-xr-x   1 root root  1843 2008-05-13 20:10 x11-common
-rwxr-xr-x   1 root root  5755 2008-05-09 11:52 mysql
-rwxr-xr-x   1 root root  2515 2008-05-09 11:52 mysql-ndb
-rwxr-xr-x   1 root root  1905 2008-05-09 11:52 mysql-ndb-mgm
-rwxr-xr-x   1 root root  2653 2008-05-02 16:41 apparmor
-rwxr-xr-x   1 root root  1492 2008-04-21 18:53 readahead
-rwxr-xr-x   1 root root  1957 2008-04-21 18:53 readahead-desktop
-rwxr-xr-x   1 root root   864 2008-04-21 18:53 stop-readahead
-rwxr-xr-x   1 root root  2287 2008-04-21 16:15 cupsys
-rwxr-xr-x   1 root root  6609 2008-04-21 03:34 bluetooth
-rwxr-xr-x   1 root root  1244 2008-04-19 01:05 mountoverflowtmp
-rwxr-xr-x   1 root root  3597 2008-04-19 01:05 bootclean
-rwxr-xr-x   1 root root  2121 2008-04-19 01:05 bootlogd
-rwxr-xr-x   1 root root  1768 2008-04-19 01:05 bootmisc.sh
-rwxr-xr-x   1 root root  3454 2008-04-19 01:05 checkfs.sh
-rwxr-xr-x   1 root root 10602 2008-04-19 01:05 checkroot.sh
-rwxr-xr-x   1 root root  1228 2008-04-19 01:05 halt
-rwxr-xr-x   1 root root   909 2008-04-19 01:05 hostname.sh
-rwxr-xr-x   1 root root   944 2008-04-19 01:05 killprocs
-rwxr-xr-x   1 root root   596 2008-04-19 01:05 mountall-bootclean.sh
-rwxr-xr-x   1 root root  2430 2008-04-19 01:05 mountall.sh
-rwxr-xr-x   1 root root  1465 2008-04-19 01:05 mountdevsubfs.sh
-rwxr-xr-x   1 root root  1544 2008-04-19 01:05 mountkernfs.sh
-rwxr-xr-x   1 root root   594 2008-04-19 01:05 mountnfs-bootclean.sh
-rwxr-xr-x   1 root root  3123 2008-04-19 01:05 mtab.sh
-rwxr-xr-x   1 root root  7891 2008-04-19 01:05 rc
-rwxr-xr-x   1 root root   522 2008-04-19 01:05 rc.local
-rwxr-xr-x   1 root root   117 2008-04-19 01:05 rcS
-rw-r--r--   1 root root  1335 2008-04-19 01:05 README
-rwxr-xr-x   1 root root   692 2008-04-19 01:05 reboot
-rwxr-xr-x   1 root root  1000 2008-04-19 01:05 rmnologin
-rwxr-xr-x   1 root root  1199 2008-04-19 01:05 sendsigs
-rwxr-xr-x   1 root root   585 2008-04-19 01:05 single
-rwxr-xr-x   1 root root  4215 2008-04-19 01:05 skeleton
-rwxr-xr-x   1 root root   510 2008-04-19 01:05 stop-bootlogd
-rwxr-xr-x   1 root root   647 2008-04-19 01:05 stop-bootlogd-single
-rwxr-xr-x   1 root root  4030 2008-04-19 01:05 umountfs
-rwxr-xr-x   1 root root  1833 2008-04-19 01:05 umountnfs.sh
-rwxr-xr-x   1 root root  1863 2008-04-19 01:05 umountroot
-rwxr-xr-x   1 root root  1815 2008-04-19 01:05 urandom
-rwxr-xr-x   1 root root  2445 2008-04-19 01:05 waitnfs.sh
-rwxr-xr-x   1 root root   693 2008-04-19 00:42 policykit
-rwxr-xr-x   1 root root  2710 2008-04-19 00:19 acpid
-rwxr-xr-x   1 root root  1935 2008-04-16 08:49 firestarter
-rwxr-xr-x   1 root root  4528 2008-04-14 23:36 hwclockfirst.sh
-rwxr-xr-x   1 root root  4521 2008-04-14 23:36 hwclock.sh
-rwxr-xr-x   1 root root   820 2008-04-14 03:51 vbesave
-rwxr-xr-x   1 root root   723 2008-04-11 13:15 cryptdisks
-rwxr-xr-x   1 root root   681 2008-04-11 13:15 cryptdisks-early
-rwxr-xr-x   1 root root  2488 2008-04-11 08:21 udev
-rwxr-xr-x   1 root root   706 2008-04-11 08:21 udev-finish
-rwxr-xr-x   1 root root  4945 2008-04-10 20:12 rsync
-rwxr-xr-x   1 root root  3576 2008-04-10 12:49 hotkey-setup
-rwxr-xr-x   1 root root  1761 2008-04-08 14:02 cron
-rwxr-xr-x   1 root root  1793 2008-04-06 21:18 pulseaudio
-rwxr-xr-x   1 root root  7195 2008-04-04 19:38 glibc.sh
-rwxr-xr-x   1 root root   568 2008-03-30 01:41 xserver-xorg-input-wacom
-rwxr-xr-x   1 root root  1795 2008-03-27 19:23 brltty
-rwxr-xr-x   1 root root  5647 2008-03-27 12:24 dkms_autoinstaller
-rwxr-xr-x   1 root root  2594 2008-03-21 06:38 avahi-daemon
-rwxr-xr-x   1 root root  1261 2008-03-13 18:24 procps
-rwxr-xr-x   1 root root  1626 2008-03-12 17:27 wpa-ifupdown
-rwxr-xr-x   1 root root   177 2008-03-08 19:24 powernowd.early
-rwxr-xr-x   1 root root  4721 2008-03-08 19:24 powernowd
-rwxr-xr-x   1 root root  1573 2008-03-07 15:22 ntp
-rwxr-xr-x   1 root root  9708 2008-02-27 08:22 alsa-utils
-rwxr-xr-x   1 root root  1399 2008-02-25 16:20 module-init-tools
-rwxr-xr-x   1 root root  1634 2008-01-28 12:49 console-setup
-rwxr-xr-x   1 root root  1376 2008-01-28 12:49 keyboard-setup
-rwxr-xr-x   1 root root  2327 2008-01-19 22:44 timidity
-rwxr-xr-x   1 root root  2308 2007-12-11 18:00 laptop-mode
-rwxr-xr-x   1 root root  1772 2007-12-03 15:50 networking
-rwxr-xr-x   1 root root  1729 2007-11-23 04:06 klogd
-rwxr-xr-x   1 root root  3343 2007-11-23 04:06 sysklogd
-rwxr-xr-x   1 root root   860 2007-11-21 13:31 nvidia-kernel
-rwxr-xr-x   1 root root  2377 2007-10-23 13:03 pcmciautils
-rwxr-xr-x   1 root root   955 2007-10-23 12:01 screen-cleanup
-rwxr-xr-x   1 root root  1506 2007-10-23 10:34 dhcdbd
-rwxr-xr-x   1 root root  2814 2007-10-15 05:20 usplash
-rwxr-xr-x   1 root root   375 2007-10-04 15:56 pppd-dns
-rwxr-xr-x   1 root root   762 2007-08-30 22:48 acpi-support
-rwxr-xr-x   1 root root  1223 2007-06-22 00:55 dns-clean
-rwxr-xr-x   1 root root  6355 2007-05-30 08:29 console-screen.sh
-rwxr-xr-x   1 root root  1667 2007-05-23 08:59 apmd
-rwxr-xr-x   1 root root   969 2007-02-20 08:41 atd
-rwxr-xr-x   1 root root   927 2006-04-27 01:08 wifi-radar
-rwxr-xr-x   1 root root   748 2006-01-23 13:47 loopback
-rwxr-xr-x   1 root root  1109 2005-10-27 08:15 binfmt-support
rich@rich-desktop:~$ 

I believe the original instructions on the MythTV page were as follows

Installing MythTV
MythTV Packages

To install MythTV , simply click on the following link: Install MythTV

...this installs MythTV and all other required packages, including the MySQL database.

Alternatively, you can install by hand:

sudo apt-get update
sudo apt-get install mythtv

Either way, it will take a few minutes to download and install. If you are using Hardy, there have been a number of improvements to the installation process. It now pops up a few dialogues:

    * It will ask you for a password for the MySQL root user. It is strongly recommended that you leave this blank. Specifying a password here has been known to cause database access problems later on. It may seem insecure, but on your home network should be okay.
    * The second screen gives some information regarding running mythtv-setup to complete the process - we'll go through that in the next section.
    * It then asks whether you want to allow remote connections to your backend. As a rule, that's not something I would usually recommend (ouch!), but as long as your MythTV box is behind a firewall I suggest that you answer "Yes" - it will make it much easier if you want to add a separate frontend in the future.
    * It then asks you again whether you want to specify a password for the MySQL root user. Again leave this blank unless you know what you're doing. 

[http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)

I am not sure how to go back and change it if I should be using a password.

---

### Post by volkswagner on 2008-09-24
Well it looks like mysql is running.

Try to login with no root password.

```
mysql -u root
```

or

```
mysql -u root mysql
```

or

```
mysql -u root -p
```
and leave the password blank.

You can change/set the password.

[http://ubuntu.flowconsult.at/en/mysql-set-change-reset-root-password/]("http://ubuntu.flowconsult.at/en/mysql-set-change-reset-root-password/")

[http://www.cyberciti.biz/faq/mysql-change-root-password/]("http://www.cyberciti.biz/faq/mysql-change-root-password/")

EDIT:  I don't want to add confusion, but check this out.
[http://ubuntuforums.org/showthread.php?t=305018]("http://ubuntuforums.org/showthread.php?t=305018")

---

### Post by Buschbarber on 2008-09-24
rich@rich-desktop:~$ mysql -u root
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 7
Server version: 5.0.51a-3ubuntu5.1 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> 

Now what?

I will look at the links you posted.

---

### Post by Buschbarber on 2008-09-24
I followed the first link to change the password and typed in the command as writen, being case sensitive, and received the following error

ERROR 1046 (3D000): No database selected
Query OK, 0 rows affected (0.00 sec)

Bye
rich@rich-desktop:~$

---

### Post by volkswagner on 2008-09-24
Try the mysqladmin instructions, ie:second link.

If there is no current password you should be able to run
```

$ mysqladmin -u root password NEWPASSWORD
``` 

edit to suite what you want the root password to be in place of "NEWPASSWORD". 

If that works you will still need to run
```
sudo dpkg-reconfigure mysql-server
```

And also the steps in post #4 of the following.

[http://ubuntuforums.org/showthread.php?t=600315&highlight=backend+mysql]("http://ubuntuforums.org/showthread.php?t=600315&highlight=backend+mysql")


If mythtv still cant connect, you need to make sure you can log into mysql using the new password for mythv

```
mysql -u mythtv -p 
```
and make sure your password works here.  If it does not work you may need to set the  mysql  password for mythtv user.  Use the mysqladmin instructions.

---

### Post by Buschbarber on 2008-09-24
I got as far as these steps.

rich@rich-desktop:~$ mysqladmin -u root password MYpalin
rich@rich-desktop:~$ sudo dpkg-reconfigure mysql-server
[sudo] password for rich: 
rich@rich-desktop:~$ sudo dpkg-reconfigure mysql-server
rich@rich-desktop:~$ rm ~/.mythtv -rf && rm /home/mythtv/.mythtv -rf
rm: cannot remove `/home/mythtv/.mythtv/mysql.txt': Permission denied
rich@rich-desktop:~$ sudo rm ~/.mythtv -rf && rm /home/mythtv/.mythtv -rf
rm: cannot remove `/home/mythtv/.mythtv/mysql.txt': Permission denied
rich@rich-desktop:~$

---

### Post by anonymousdog on 2008-09-25
> **Buschbarber said:**
> rich@rich-desktop:~$ sudo rm ~/.mythtv -rf && rm /home/mythtv/.mythtv -rf
rm: cannot remove `/home/mythtv/.mythtv/mysql.txt': Permission denied
rich@rich-desktop:~$
You need```
sudo rm /home/mythtv/.mythtv -rf
```then proceed with whatever steps you were following.

---

### Post by Buschbarber on 2008-09-25
I was able to login to mysql with a Blank password. Apparently I was unsuccessful in changing it. Is it necessary to have a Non-Blank password?
This is where I am now

rich@rich-desktop:~$ sudo rm /home/mythtv/.mythtv .rf
[sudo] password for rich: 
rm: cannot remove `/home/mythtv/.mythtv': Is a directory
rm: cannot remove `.rf': No such file or directory
rich@rich-desktop:~$ sudo rm /home/mythtv/.mythtv -rf
rich@rich-desktop:~$ rm ~/.mythtv -rf && rm /home/mythtv/.mythtv -rf
rich@rich-desktop:~$ sudo dpkg-reconfigure mythtv-database
Failed to connect to database: Can't connect to MySQL server on 'rich-desktop' (111) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
It's also possible that mysql-server wasn't running.  After install
is completed, you will need to make sure mysql-server is running
and that you supplied correct information. Try:
sudo dpkg-reconfigure mythtv-database
rich@rich-desktop:~$ sudo dpkg-reconfigure mythtv-database
Failed to connect to database: Can't connect to MySQL server on 'rich-desktop' (111) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
It's also possible that mysql-server wasn't running.  After install
is completed, you will need to make sure mysql-server is running
and that you supplied correct information. Try:
sudo dpkg-reconfigure mythtv-database
rich@rich-desktop:~$ sudo dpkg-reconfigure mysql-server
rich@rich-desktop:~$ mysql -u mythtv -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'mythtv'@'localhost' (using password: YES)
rich@rich-desktop:~$ mysql -u mythtv -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 13
Server version: 5.0.51a-3ubuntu5.1 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> 

Where do I go from here? I am really confused as I am so new to this, but I have lots of patience.

---

### Post by Buschbarber on 2008-09-25
I tried to run the Backend Setup for MythTV. See the attached screen capture.

I was able to reset the password for MythTV using the following

sudo dpkg-reconfigure mythtv-common

I am not sure why I get the error below

rich@rich-desktop:~$ sudo dpkg-reconfigure mythtv-database
[sudo] password for rich: 
Failed to connect to database: Can't connect to MySQL server on 'rich-desktop' (111) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
It's also possible that mysql-server wasn't running.  After install
is completed, you will need to make sure mysql-server is running
and that you supplied correct information. Try:
sudo dpkg-reconfigure mythtv-database
rich@rich-desktop:~$ sudo dpkg-reconfigure mythtv-database
Failed to connect to database: Can't connect to MySQL server on 'rich-desktop' (111) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
It's also possible that mysql-server wasn't running.  After install
is completed, you will need to make sure mysql-server is running
and that you supplied correct information. Try:
sudo dpkg-reconfigure mythtv-database
rich@rich-desktop:~$ sudo dpkg-reconfigure mythtv-common
rich@rich-desktop:~$

---

### Post by volkswagner on 2008-09-25
Can you log into mysql using mythtv user, and the password you set?
```

mysql -u mythtv -p
```

---

### Post by Buschbarber on 2008-09-25
When I log into mysql as the mythtv user, I tried first, with the mythtv password and second, with no password. No password worked.

rich@rich-desktop:~$ msql -u mythtv -p
bash: msql: command not found
rich@rich-desktop:~$ mysql -u mythtv -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'mythtv'@'localhost' (using password: YES)
rich@rich-desktop:~$ mysql -u mythtv -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 15
Server version: 5.0.51a-3ubuntu5.1 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql>

---

### Post by DesiSinger on 2008-09-25
> **Buschbarber said:**
> Here are the contents of the mythsql.txt file. It still will not 

DBHostName=rich-desktop

# By default, Myth tries to ping the DB host to see if it exists.
# If your DB host or network doesn't accept pings, set this to no:
#
DBHostPing=no

DBUserName=mythtv
DBPassword=
DBName=mythconverg
DBType=QMYSQL3

# Set the following if you want to use something other than this
# machine's real hostname for identifying settings in the database.
# This is useful if your hostname changes often, as otherwise you
# will need to reconfigure mythtv (or futz with the DB) every time.
# TWO HOSTS MUST NOT USE THE SAME VALUE
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

Whether or not I run the Frontend or Backend Setup, it still refuses to allow me to Login to the DB. I am not using a password, per the instructions.


Buschbarber,

Hi, I just read the first two post of yours and wanted to ask you to try the following: 

$> mysql -u mythtv -p mythconverg
$> Enter Password: <leave it blank and click enter>

In above I'm asking you to leave the password blank as your mysql.txt file shows that the password is blank. 
This is long thead and sorry I did not read all suggestions. Please ignore if this has already been suggested. I'm able to login with the above method and have no issues.

---

### Post by Buschbarber on 2008-09-25
rich@rich-desktop:~$ mysql -u mythtv -p mythconverg
Enter password: 
ERROR 1044 (42000): Access denied for user ''@'localhost' to database 'mythconverg'

---

### Post by volkswagner on 2008-09-26
I have no experience with a blank password for mythtv.  You need to verify mythconverge database is installed.

Try the previous suggestion with root user.  If mythconverge is not there you will have to manually add it to mysql.

---

### Post by Buschbarber on 2008-09-26
It is mysql that has the blank password. I have been able to login to mysql with a blank password
mythtv has a password that I was able to set.

Remember, I am new to linux. When you say "Try the previous as root user", I assume you mean preface the command with sudo?

I entered the following, in Terminal. In the first attempt, I entered the password for the root and then left the other password blank.
In the second attempt, I entered the mythtv password.

Same results

Does it matter that mysql has a blank password. If it matters, how do I change it from blank to a password.

Please be specific with the code as it is easier to follow without making a mistake.

For example - I was told to use the following command to change the mysql password

rich@rich-desktop:~$ mysqladmin -u root password 'Newpassword'

I typed in the above command, replacing 'Newpassword' with the password I wanted to use (without the quotes of course). When I hit enter, there was no acknowledgment that that anything had changed, and no error message. so I assumed that the password was changed

rich@rich-desktop:~$

I just tried to execute the same command to change the password and I got an error

I still was able to run mysql without using a password

rich@rich-desktop:~$ sudo mysqladmin -u root password imlost
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'
rich@rich-desktop:~$ mysql
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 29
Server version: 5.0.51a-3ubuntu5.1 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql>

---

### Post by volkswagner on 2008-09-26
Sorry, I need to be short.  You need to set/change mythtv password in mysql, to the password you assigned earlier.

EDIT: Post the results for the following

mysql -u root -p

      mysql> show databases;

      mysql> quit

---

### Post by Buschbarber on 2008-09-26
Here are the results of the commands you asked me to excute

rich@rich-desktop:~$ mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 41
Server version: 5.0.51a-3ubuntu5.1 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema | 
| mysql              | 
+--------------------+
2 rows in set (0.02 sec)

mysql> quit
Bye
rich@rich-desktop:~$ 

Once again, I am a bit confused. 

Let me get the password situation straight. Tell me if the following is true or false

I use a password to log into Linux as Rich(is this the same as the Root password, as well?)
I need to use a password to log in to mysql?
I need to use a password to log in to mythtv?

When I type mysql, at the Prompt, I am not prompted for a password
When I type mysql -u root -p, I am prompted for a password. Is that supposed to be the Root password?

Does it matter if I set All the passwords I need to use, to the same password, or do they all have to be different?

Are there situations when I can leave a password as Blank?

When I installed MythTV, I set up a password that was the same as the password I use to login to Linux and it is also the same password I use to login as Root

---

### Post by volkswagner on 2008-09-26
> **Buschbarber said:**
> Here are the results of the commands you asked me to excute

rich@rich-desktop:~$ mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 41
Server version: 5.0.51a-3ubuntu5.1 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema | 
| mysql              | 
+--------------------+
2 rows in set (0.02 sec)

mysql> quit
Bye
rich@rich-desktop:~$ 

As you can see above, mythconverg was not created in mysql.  This will need to be created.  Running "sudo dpkg-reconfigure mythtv-database" may get it done.

> Once again, I am a bit confused. 

Let me get the password situation straight. Tell me if the following is true or false

I use a password to log into Linux as Rich(is this the same as the Root password, as well?)

When you install Linux, two users should be created. Rich a person with his password.  Root or super user ("a virtual user with super power"), shall have a unique password.

Try this, change to root user, and look at the new command prompt.  My root password is different than eric.  Exit when done.  SU shall not be taken lightly.

It should be noted, you cant log into the system with your root account.  You can switch inside a terminal.

```
su
```

Here is mine.
```
eric@Web:~$ su
Password: secret
root@Web:/home/eric# 
```

I am not sure if Ultimate Edition, handles the install differently.  I can't access root on my 1.6 install, not sure why.  The example is from 6.06 server.

> I need to use a password to log in to mysql?
Only if you set passwords, choice is during mysql setup, or post install.

> I need to use a password to log in to mythtv?
You don't need a password to log into mythtv.  Mythtv is run by the mythtv user, who needs access to mysql database mythconverge.  Password rules are the same as for root user.  You decide.  Most people want the security of passwords on systems connected to the web.

> When I type mysql, at the Prompt, I am not prompted for a password
When I type mysql -u root -p, I am prompted for a password. Is that supposed to be the Root password?
Using the "p-" is telling mysql to use password for access.  This is only needed when passwords are setup for mysql.  If passwords are not setup the "-p" is not needed, in fact an error will occur if password is not set.  The password inserted will be for the user you specify, root, Rich, mythtv, etc.  The user root can have a different password for mysql, vs. his linux password. 

> Does it matter if I set All the passwords I need to use, to the same password, or do they all have to be different?

This question is beyond my knowledge.  My opinion says, unique passwords are best.  

> Are there situations when I can leave a password as Blank?

What ever floats your boat, I guess.

> When I installed MythTV, I set up a password that was the same as the password I use to login to Linux and it is also the same password I use to login as Root

Easy to remember huh?

I hope I cleared a little.

---

### Post by Buschbarber on 2008-09-27
With regards to the passwords, I guessed as much, but I just wanted to be sure.

I was unable to get mythconverg added because when I executed the code you specified, I get the following error

rich@rich-desktop:~$ sudo dpkg-reconfigure mythtv-database
Failed to connect to database: Can't connect to MySQL server on 'rich-desktop' (111) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
It's also possible that mysql-server wasn't running.  After install
is completed, you will need to make sure mysql-server is running
and that you supplied correct information. Try:
sudo dpkg-reconfigure mythtv-database

I seem to remember trying this before and receiving the same error message. I tried using both root and rich as the msql admin

---

### Post by Buschbarber on 2008-09-27
I tried to follow the procedure to reset the MySQL password.

rich@rich-desktop:~$ sudo /etc/init.d/mysql stop
 * Stopping MySQL database server mysqld                                        080927  1:30:07 [Note] mysqld: Normal shutdown

080927  1:30:07  InnoDB: Starting shutdown...
080927  1:30:09  InnoDB: Shutdown completed; log sequence number 0 43655
080927  1:30:09 [Note] mysqld: Shutdown complete

                                                                         [ OK ]
[1]+  Done                    sudo mysqld --skip-grant-tables
rich@rich-desktop:~$ sudo mysqld --skip-grant-tables &
[1] 30693
rich@rich-desktop:~$ 080927  1:30:25  InnoDB: Started; log sequence number 0 43655
080927  1:30:25 [Note] mysqld: ready for connections.
Version: '5.0.51a-3ubuntu5.1'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)
mysql -u root mysql
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 1
Server version: 5.0.51a-3ubuntu5.1 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> UPDATE user SET Password='secret' where User='root'; FLUSH PRIVILEGES; exit;
Query OK, 0 rows affected (0.00 sec)
Rows matched: 3  Changed: 0  Warnings: 0

080927  1:32:46 [Warning] Found invalid password for user: 'root@localhost'; Ignoring user
080927  1:32:46 [Warning] Found invalid password for user: 'root@rich-desktop'; Ignoring user
080927  1:32:46 [Warning] Found invalid password for user: 'root@127.0.0.1'; Ignoring user
Query OK, 0 rows affected (0.00 sec)

Bye

---

### Post by volkswagner on 2008-09-27
I am no expert with mysql.  Was that all on one line?  Try the following, it is slightly different.  Hit enter after each semi-colon (not sure if it makes a difference).  Don't worry about the previous stuff.  Try it this way.

```
rich@rich-desktop:~$ mysql -u root mysql
```

```
mysql> UPDATE user SET Password=PASSWORD('putnewrootpasshere') WHERE user='root';
```


```
mysql> FLUSH PRIVILEGES;
```

```
mysql> quit;
```

```
rich@rich-desktop:~$ mysql -u -root -p mysql
```
Try your new password.

If it works do the same thing except change user='mythtv' and give him a unique password.   

Then for fun sake run

```
rich@rich-desktop:~$ sudo /etc/init.d/mysql restart
```

Make sure you can still log into mysql with new passwords.

Then use the new passwords when running....The following.

```
rich@rich-desktop:~$ sudo dpkg-reconfigure mythtv-database
```

---

### Post by Buschbarber on 2008-09-27
OK!! After I was successful in typing the code, with the Proper Syntax, in the order you specified, I was able to change the MySQL passwords for root and mythtv. The problem is, when I now try to reconfigure the mythtv-database, I get the following error. Just to check, I logged into mysql with the new password for root, and it still worked fine.

rich@rich-desktop:~$ sudo dpkg-reconfigure mythtv-database
Failed to connect to database: Can't connect to MySQL server on 'rich-desktop' (111) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
It's also possible that mysql-server wasn't running.  After install
is completed, you will need to make sure mysql-server is running
and that you supplied correct information. Try:
sudo dpkg-reconfigure mythtv-database
rich@rich-desktop:~$ mysql -u root -p mysql
Enter password: 
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 7
Server version: 5.0.51a-3ubuntu5.1 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql>

---

### Post by volkswagner on 2008-09-27
Try this. Going back a bit.

```
sudo rm ~/.mythtv -rf && rm /home/mythtv/.mythtv -rf
```

```
sudo dpkg-reconfigure mythtv-database
```

If that fails, try

```
sudo dpkg-reconfigure mysql-server
```

If that works then

sudo dpkg-reconfigure mythtv-common

Using the passwords you set in mysql.

---

### Post by Buschbarber on 2008-09-27
rich@rich-desktop:~$ sudo rm ~/.mythtv -rf && rm /home/mythtv/.mythtv -rf
rm: cannot remove `/home/mythtv/.mythtv/mysql.txt': Permission denied
rich@rich-desktop:~$ sudo dpkg-reconfigure mythtv-database
Failed to connect to database: Can't connect to MySQL server on 'rich-desktop' (111) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
It's also possible that mysql-server wasn't running.  After install
is completed, you will need to make sure mysql-server is running
and that you supplied correct information. Try:
sudo dpkg-reconfigure mythtv-database
rich@rich-desktop:~$ sudo dpkg-reconfigure mysql-server
rich@rich-desktop:~$ sudo dpkg-reconfigure mythtv-common
rich@rich-desktop:~$

---

### Post by volkswagner on 2008-09-28
You seem to have root user problems.  Can you access your root account, as I mentioned above (post #32)?

```
su
```
enter root password, do you get a root user command prompt?

---

### Post by Buschbarber on 2008-09-28
I have not had any problems, that I know of, logging in as root. Whenever I use the sudo code, it prompts me for my root password and accepts it.

rich@rich-desktop:~$ su
Password: 
root@rich-desktop:/home/rich# 

I currently use the same password for root and rich, however, I did change the password for mysql and mythtv so they are different from each other and different from root and rich

By the way, I was given the method to set up a login as root, by someone else. I was warned to be careful and not say logged in too long. I have only done it a couple of times.

You can log in as root(however, be careful and take your time).
This is how you do it:
Start menu:
Adminstration
Login Window
Security
check allow local system adminstrator login
next:
Start menu
Adminstration
Users and groups
click on root and unlock using your password
properties for root account
set password by hand
click ok
Now you can log in as root and do whatever you want.
Just make sure you log out when you are done and log back in as yourself when you are done tinkering. Only insane people like myself stay logged in as root for long periods of time(security issues and all that).
Hope you everything up and running shortly.

---

### Post by volkswagner on 2008-09-28
This is turning into a real bugger.  If the following does not work, start new thread with the following heading.

rm: cannot remove `/home/mythtv/.mythtv/mysql.txt': Permission denied

My earlier post was supposed to include an additional mythtv-database reconfigure with --force option.  I can't find the correct syntax at the moment, so I apologize for that.

OK, try this,

```
sudo nano /home/mythtv/.mythtv/mysql.txt
```

Then edit the password field to your new password.  I am not sure if you have used nano before.  The command short cuts are at the bottom.  When you are done editing

ctrl+o writes your changes, then enter accepts changes, and ctrl+x exits the editor.

Then try
```

sudo dpkg-reconfigure mythtv-database
```

if that fails then

```
sudo dpkg-reconfigure --force mythtv-database
```

QUESTION.....What happens when you run the above, do you get the "x-window" pop-up or just returned to new line in the shell (nothing)?


One more thing to try, at your own risk.  Open the file manager as root and manually delete mysql.txt.

```
sudo thunar
```

Navigate to /home/mythtv/.mythtv/ and delete mysql.txt.

You will need to enable show hidden folders under the "view" tab.

Then exit thunar, and try again, reconfigure mythtv-database.....

---

### Post by Buschbarber on 2008-09-28
Here are the contents of the mysql.txt file. I had originally opened it by navigating to it using Places/File System/Home/mythtv/.mythtv and double-clicked on the file mysql.txt. It already had the correct password, at the bottom, for the mythtv user

DBHostName=rich-desktop

# By default, Myth tries to ping the DB host to see if it exists.
# If your DB host or network doesn't accept pings, set this to no:
#
DBHostPing=no

DBUserName=mythtv
DBName=mythconverg
DBType=QMYSQL3

# Set the following if you want to use something other than this
# machine's real hostname for identifying settings in the database.
# This is useful if your hostname changes often, as otherwise you
# will need to reconfigure mythtv (or futz with the DB) every time.
# TWO HOSTS MUST NOT USE THE SAME VALUE
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
DBPassword=secret

I followed your instructions to open the file with nano, but it did not display the contents of the file and I did not know how to do so, however, the password was correct, so I closed nano.

I proceeded to run the other codes with the usual result

rich@rich-desktop:~$ sudo nano /home/mythtv/.mythtv/msql.txt
[sudo] password for rich: 
rich@rich-desktop:~$ sudo nano /home/mythtv/.mythtv/msql.txt
rich@rich-desktop:~$ sudo dpkg-reconfigure mythtv-database
Failed to connect to database: Can't connect to MySQL server on 'rich-desktop' (111) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
It's also possible that mysql-server wasn't running.  After install
is completed, you will need to make sure mysql-server is running
and that you supplied correct information. Try:
sudo dpkg-reconfigure mythtv-database
rich@rich-desktop:~$ sudo dpkg-reconfigure --force mythtv-database
Failed to connect to database: Can't connect to MySQL server on 'rich-desktop' (111) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
It's also possible that mysql-server wasn't running.  After install
is completed, you will need to make sure mysql-server is running
and that you supplied correct information. Try:
sudo dpkg-reconfigure mythtv-database

When I runsudo dpkg-reconfigure, it brings up what I guess you call an X-Window.

The parameter fields are already filled in and I hit Enter after each field is displayed

Host of MySQL server - rich-desktop
MySQL Admin - root
Password for MySQL admin -  root (I type in the mysql password I created for root)
Will any other computers be running MythTv - no (this is the default

I am then out of X-Window and back to Terminal with the error message we keep seeing.

I deleted the mysql.txt file, so I do not know where to go from here

I will start the new thread as you suggest. Will you still respond to this thread?

---

### Post by volkswagner on 2008-09-28
I must admit I am running out of Ideas.  This has gone way beyond my skill level.

My best guess is, your root password is not set properly. 

you could try running the command as root in a different manner to see if it changes things.

```
su
```
enter root password
```

dpkg-reconfigure --force mythtv-database
```

If that fails maybe create a new thread named

Failed to create database (incorrect admin username/password?)

---

### Post by Buschbarber on 2008-09-29
OK!!! I took a shot and Reinstalled the OS.

After adding the Updates and configuring the Desktop look, I Installed MythTV from Synaptic.

I do not remember doing this before, but I had to go into Users and Groups. Unlock the Root user, and set the password for Root.

I ran MythTV Backend setup and it again told me it Could not login to the Database.

I next did the following


Code:

su

enter root password
Code:

dpkg-reconfigure --force mythtv-database

It did not return an error so I ran the MythTV Backend setup and this time it brought up all the configuration screens

By the way, I made sure all the passwords were different.

I have the WinTV HVR 1600 PCI card. The question now is how do I configure it to display Live TV? I am not sure it is recognizing the card. It worked fine when I was in Windows XP MCE.

---

### Post by Buschbarber on 2008-09-30
I was directed, by a friend, to the following site, to install the proper drivers for my WinTV HVR 1600 card and the MythTV Backend setup. I believe I was successful installing the drivers and firmware

[http://www.mythtv.org/wiki/index.php/Hauppauge_HVR-1600](http://www.mythtv.org/wiki/index.php/Hauppauge_HVR-1600)

I followed the instructions on the page. I rebooted and ran the command to see if the card was recognized.

rich@rich-desktop:~$ dmesg | grep cx18
[   41.485518] cx18:  Start initialization, version 1.0.0
[   41.485580] cx18-0: Initializing card #0
[   41.485585] cx18-0: Autodetected Hauppauge card
[   41.485873] cx18-0: cx23418 revision 01010000 (B)
[   41.870502] cx18-0: Autodetected Hauppauge HVR-1600
[   41.870505] cx18-0: VBI is not yet supported
[   42.184604] tuner 1-0061: chip found @ 0xc2 (cx18 i2c driver #0-1)
[   42.184647] cs5345 0-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[   42.384149] cx18-0: Disabled encoder IDX device
[   42.384206] cx18-0: Registered device video0 for encoder MPEG (2 MB)
[   42.384210] DVB: registering new adapter (cx18)
[   42.533090] cx18-0: DVB Frontend registered
[   42.533134] cx18-0: Registered device video32 for encoder YUV (2 MB)
[   42.533172] cx18-0: Registered device video24 for encoder PCM audio (1 MB)
[   42.533177] cx18-0: Initialized card #0: Hauppauge HVR-1600
[   42.533205] cx18:  End initialization
[   63.388887] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[   63.956419] cx18-0: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
[   63.962762] cx18-0: FW version: 0.0.74.0 (Release 2007/03/12)
[   65.143855] cx18-0: loaded v4l-cx23418-dig.fw firmware (16382 bytes)
rich@rich-desktop:~$
It looks like it is recognized. This is a Beta. It mentions I have to redo some steps whenever the Kernel changes.

Next step is to configure MythTV

Well I got as far as Scanning for Channels, but that portion of the Config screen is greyed out, so I cannot go any further.
Like all instructions, they do not use the same exact words to describe the same thing, so you have to interpret what they are saying.

It says to configure the Analog and the Digital halves of the card.
It says to choose New Capture card and choose Mpeg2 Encoder, and so on
It now says to choose a new Tuner card - There is not option for new  Tuner card, only new Capture card
I choose a new Capture card and choose DVB DTV and so on.
I go back to the Main Menu and select Input connections
I choose DVB0, but Scan for Channels is greyed out

---

### Post by Buschbarber on 2008-09-30
I don't know if it is the Color Scheme I have chosen, but when I am in the MythTV Backend Setup, there are some parameter fields that highlite in Orange, and others that do not highlite at all, like the Video Source parameter.

When I use the Right Arrow key, the word None disappears and the Scan Channels and Fetch Channels fields become Ungreyed.

I was able to Scan Channels for both the Analog and Digital halves of the card. It just found a signal on channels 2-99 for the Analog side of the card.

I have Time Warner Digital Cable, but the card is connected to cable into the house and not to the cablebox.

Also, this card has one coax connector for cable and one for HD via an antenna. I do not have an antenna and I do not believe I can connect my cable coax to the antenna coax connector. At least I could not get a signal, in Windows, when connecting the cable to the Antenna coax connector.

---

### Post by volkswagner on 2008-09-30
You should do a little research on your card.

[http://ubuntuforums.org/search.php?searchid=48838919]("http://ubuntuforums.org/search.php?searchid=48838919")

Post a new thread if you need to.  

You should mark this thread as solved, via the tread tools button.  

I had a hunch the password was not set correctly.  I did not want to be the one to suggest a reinstall. I guess it is often necessary though.  If not, at least it can be quicker.

Kill all commercials!

---

### Post by Buschbarber on 2008-09-30
Thank you very much for sticking with me and guiding me through the debugging process.

A local radio show I listen to, called SoundBytes, is hosted by one of my firend's cousins, Nick Francesco. He is always encouraging people to use Linux. Lately, he promotes Ubuntu. I finally decided to dual boot Linux with Windows. Ultimate is so much faster than Windows XP MCE, on the same machine. Even the OS install is so much faster. Access to additional software, drivers, and updates is so easy and fast. I do not know what half of the commands are that I am typing in, but so far, the typos have been few. In the 80's I used to type in Basic programs that were published in a magazine, just to get new software.

I have MythTV up and running. I am just learning how to use the interface. I have used WinTV, BeyondTV, SageTV, and Pinnacle PCTV, under Windows, as well as Windows Media Center.

Is it true that I have to pay $20/yr to get a Program Guide that will work with MythTV?

Does MythTV allow you to Skip Commercials, when Recording?

---

### Post by volkswagner on 2008-10-01
> **Buschbarber said:**
> 
I have MythTV up and running. I am just learning how to use the interface. I have used WinTV, BeyondTV, SageTV, and Pinnacle PCTV, under Windows, as well as Windows Media Center.

Is it true that I have to pay $20/yr to get a Program Guide that will work with MythTV?

Does MythTV allow you to Skip Commercials, when Recording?

I have not tried this for free guide data.  I set up schedules direct before knowledge of this.

[http://ubuntuforums.org/showthread.php?t=862816&highlight=free+guide+data]("http://ubuntuforums.org/showthread.php?t=862816&highlight=free+guide+data")

Yes, Mythtv has commskip, you need to enable it.  You can set it up for each recording, or global in backend setup, "allow commskip".  If you set it up global, you can turn it off for commercial free channels, etc.

---

### Post by Buschbarber on 2008-10-01
Is there a way to use a Mouse to navigate the MythTV screens? It requires quite a bit of keyboard strokes.

---

