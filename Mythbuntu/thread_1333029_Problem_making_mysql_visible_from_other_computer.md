---
title: "Problem making mysql visible from other computer"
date: 2009-11-21
forum: Mythbuntu
---

### Post by Elv13 on 2009-11-21
Hi, 

I edited /etc/mysql/my.conf and changed the bind adress from 127.0.0.1 to 192.168.2.238 in order to be able to use other frontend, but I can't connect anymore.

> mysql -u root --password="myPassword" -h 192.168.2.238
ERROR 1045 (28000): Access denied for user 'root'@'lepagee-mediaserver.local' (using password: YES)

The strange thing is that I can still connect on localhost:
```
mysql -u root --password="mypassword" -h 127.0.0.1
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 344
Server version: 5.1.37-1ubuntu5 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql>
```

So the change did not worked. Here is my /etc/mysql/my.cnf:
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
pid-file	= /var/run/mysqld/mysqld.pid
socket		= /var/run/mysqld/mysqld.sock
port		= 3306
basedir		= /usr
datadir		= /var/lib/mysql
tmpdir		= /tmp
skip-external-locking
#
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
bind-address		= 192.168.2.238
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
#
# Error logging goes to syslog due to /etc/mysql/conf.d/mysqld_safe_syslog.cnf.
#
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

EDIT:
I get
```
mysql -u root --password="password" -h 192.168.2.238
ERROR 1045 (28000): Access denied for user 'root'@'lepagee-mediaserver.local' (using password: YES)

```

if I edit /etc/mysql/conf.d/mythtv.cnf to use 192.168.2.238

EDIT2:
I did 
sudo iptables -A INPUT -p tcp -d 0/0 -s 0/0 --dport 3306 -j ACCEPT
just in case, but it did not help.

EDIT3:
I try with the right password, the same password work with 127.0.0.1

EDIT4:
The problem may come from the fact that I executed this command:
grant all on mythconverg.* to mythtv@"%" identified by "mythtv";
I created a new database on a remote server and it worked (not mythtv, just the connection) until I executed that command.

EDIT5:
By creating a new user called mythtv2 and giving it abusive privileges, I managed to connect to it using 192.168.2.238. It work in mythtv too for my main backend, but my remote "mymote" iphone control application still fail to connect... any idea why?

---

### Post by alexyz on 2009-11-21
I think you already know this, but when defining users and privileges in mysql you also specify which hosts they're allowed to connect from.  That's the part after '@' in a clause like 'root'@'lepagee-mediaserver.local'  Can also be 'root'@'192.168.1.100';

Perhaps mysql is resolving the IP to the hostname?  I'm pretty sure you can define user/privs independently by IP and/or by hostname.  What I'm not sure of is how the mysql server "sees" the incoming connection.  If you're running a DNS it might resolve IPs to hostnames...

HTH

Edit:  I couldn't find a short clear explanation of this but the standard docs might help:  [http://dev.mysql.com/doc/refman/5.0/en/adding-users.html](http://dev.mysql.com/doc/refman/5.0/en/adding-users.html)

---

### Post by Elv13 on 2009-11-21
I use "%" am I am behind a firewall, so it was not the problem. In fact, it was much simpler. It was a bug. Avahi was telling wrong IP corresponding to hostname, so everytime lepagee-mediaserver was converted to IP or vice versa, the wrong value was returned, resulting in attempt to connect to the wrong host. As much of them have mysql installed, I did not noticed it as a MySQL server was responding to the request, but it was the wrong one. Now, I hardcoded all IPs and forced them, so it does not try to do some kind of DNS check, and now it work!

So this problem is solved.

---

