---
title: "Database restore on clean install"
date: 2011-11-29
forum: Mythbuntu
---

### Post by trevs.bronco on 2011-11-29
Hi,

I'm sure i must be missing something simple, but I am unable to get my db to restore after a clean install. I have followed the guide [here]("http://www.mythbuntu.org/upgrading"), which references [this]("http://www.mythtv.org/wiki/Database_Backup_and_Restore"). I somehow managed to dump the existing db, but everytime i try to run the restore script i get "mythconverg_restore.pl: command not found".
I'm sure i must be missing something simple, could someone please tell me what.
Thanks,

Trev

---

### Post by newlinux on 2011-11-29
what does ```
ls /usr/share/mythtv/myth*
``` return?

If it returns a file called mythconverg_restore.pl try using 
/usr/share/mythtv/mythconverg_restore.pl (full path of the command) in place of just the command

---

### Post by trevs.bronco on 2011-11-29
I'm not at home to try that command right now, but i had opened my terminal inside of that folder and could see that the script was there when i was trying to execute it. I even tried right clicking on the script in thunar and selecting "Execute" nothing apeared to happen when I did that.
I will try with the full path when I get Home.
Thanks,

Trev

---

### Post by trevs.bronco on 2011-11-29
Thanks to newlinux's suggestion i am now able to execute the script and am now at my next hurdle. running the script has got me to the point below. Everything looks correct, and it matches the myth configuration file. of the three other files listed only  
/etc/mysql/my.cnf exists and i can see nothing that contradicts the myth config file. i've attached it below for your perusal.

```
Unable to connect to database.
           database: mythconverg
               host: localhost
           username: mythtv
           password: XXXXXXXX

Please check your configuration files to verify the database connection
information is correct.  The files that are used to retrieve connection
information are prefixed with "parsing" in the "Parsing configuration files"
section of the --verbose output.

Also note that any [client] or [mysql] password specified in the MySQL options
file (/etc/my.cnf or /etc/mysql/my.cnf or ~/.my.cnf) will take precedence over
the password specified in the MythTV configuration files.
```

/etc/mysql/my.cnf
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

Thanks,

Trev

---

### Post by trevs.bronco on 2011-11-29
I'm getting closer, i reset the password to the database using post #5 of [this thread.]("http://ubuntuforums.org/showthread.php?t=611899&highlight=mythtv+backend+will")

Now I have a new error: unable to do a full restore. the database contains data.
It looks like dropping and creating the database has solved that I received a Successfully restored backup message:D
time to start the front end to see what i get.

---

