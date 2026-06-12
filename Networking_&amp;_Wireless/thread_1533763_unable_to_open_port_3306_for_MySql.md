---
title: "unable to open port 3306 for MySql"
date: 2010-07-18
forum: Networking &amp; Wireless
---

### Post by chippanfat on 2010-07-18
Hey all,
I've been working and researching this for about a week now and I still haven't had any luck.
Basically, I have been trying to open port 3306 to allow connections to my MySql server.

i've added the rule into iptables, saved and restarted that
i've added the rule into my router.
and I have removed "skip-networking" from the my.cnf file and added the blind address in, I'm trying to get this all to work on my LAN, but it doesn't seem to work, I've also restarted the entire server and then port scanned it from outside and inside the networking and it still tells me that 3306 is closed.

I did however i had some luck when I entered the Ip of the machine that would be sending data to the server but then PROFTPD stopped working and the port was open :/ im not really sure what ip should be in there but another thread from another forum said to enter the ip of the machine that mysql is installed on.
so currently its 192.168.0.2 which is the static internal address of the server.

every machine on the network has a static ip and all the rules have been added to each firewall, i.e. server and router firewalls.

ill pop my "my.cnf"  under this to see if anyone can find a mistake,

Cheers Guys !


```

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

#
# * IMPORTANT
#   If you make changes to these settings and your system uses apparmor, you may
#   also need to also adjust /etc/apparmor.d/usr.sbin.mysqld.
#

user            = mysql
pid-file        = /var/run/mysqld/mysqld.pid
socket          = /var/run/mysqld/mysqld.sock
port            = 3306
basedir         = /usr
datadir         = /var/lib/mysql
tmpdir          = /tmp
skip-external-locking
#
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.
bind-address            = 192.168.0.2
#
# * Fine Tuning
#
key_buffer              = 16M
max_allowed_packet      = 16M
thread_stack            = 128K
thread_cache_size       = 8
# This replaces the startup script and checks MyISAM tables if needed
# the first time they are touched
myisam-recover          = BACKUP
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
#log            = /var/log/mysql/mysql.log
#
# Error logging goes to syslog. This is a Debian improvement :)
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
# You might want to disable InnoDB to shrink the mysqld process by circa 100MB.
#skip-innodb
#
# * Federated
#
# The FEDERATED storage engine is disabled since 5.0.67 by default in the .cnf files
# shipped with MySQL distributions (my-huge.cnf, my-medium.cnf, and so forth).
#
skip-federated
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
# * NDB Cluster
#
# See /usr/share/doc/mysql-server-*/README.Debian for more information.
#
# The following configuration is read by the NDB Data Nodes (ndbd processes)
# not from the NDB Management Nodes (ndb_mgmd processes).
#
# [MYSQL_CLUSTER]
# ndb-connectstring=127.0.0.1


#
# * IMPORTANT: Additional settings that can override those from this file!
#   The files must end with '.cnf', otherwise they'll be ignored.
#
!includedir /etc/mysql/conf.d/

```

---

### Post by wacky_sung on 2010-07-18
Why not you show us your iptables rules as well?

Check this thread below also.
[http://www.linuxquestions.org/questions/linux-security-4/mysql-port-3306-a-55581/](http://www.linuxquestions.org/questions/linux-security-4/mysql-port-3306-a-55581/)

---

### Post by chippanfat on 2010-07-18
thanks for your reply ! :)

I think this is the part your after

```
target     prot opt source               destination
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:22
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:22
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:21
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:21
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:115
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:115
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:8080
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:8080
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:80
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:80
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:22
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:3306
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:3306
```

Im not really sure how to read it, am I being a complete beginner  in thinking that as long as it has accept then it should be alright? 
But I'm not sure why then source/destination columns are empty though
also, I've checked that thread out before, but its for the opposite situation.

Cheers.

---

