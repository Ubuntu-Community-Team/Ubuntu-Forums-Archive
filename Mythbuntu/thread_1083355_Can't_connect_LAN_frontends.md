---
title: "Can't connect LAN frontends"
date: 2009-02-28
forum: Mythbuntu
---

### Post by Weidbrewer on 2009-02-28
I had a hardware failure yesterday (CPU fried and took the mobo with it) and had to move the guts of my Myth-backend to a new machine.  I was able to restore the raid, database, etc - but now none of my three frontends can find it.  I've updated the IP address, so I know it's not that - and that has always been the solution in the past, so I'm a little lost.

---

### Post by enchesss on 2009-03-01
have you commented out the local binding in /etc/mysql/my.cnf?

---

### Post by klc5555 on 2009-03-01
> **Weidbrewer said:**
> I had a hardware failure yesterday (CPU fried and took the mobo with it) and had to move the guts of my Myth-backend to a new machine.  I was able to restore the raid, database, etc - but now none of my three frontends can find it.  I've updated the IP address, so I know it's not that - and that has always been the solution in the past, so I'm a little lost.

Might depend on the definition of "updated the IP address". I assume the three frontends can still find each other on the LAN...(?) Ideally the new backend server should be assigned the same IP address, netmask, and machine name as the blown one. Less messy. If not, the /etc/hosts file on the server and/or the clients (possibly also hosts.allow) may have to be edited to reflect the new IP address(es) and machine name(s),  And you should check to see whether the new server and the rest of the LAN are still all on the same netmask. Otherwise, your server might be connecting and routing to the internet just fine, but locally might be completely invisible in its own little parallel-universe network of one on some funky netmask value.

---

### Post by Weidbrewer on 2009-03-01
enchesss:  Could you please elaborate on what you mean by that?  There were a few things that I'd read on that, but I'm not sure what needs to be done, or how.

klc5555:  I'd need the same from you, and much more,  Everything just went right over my head.  :)

What should I be looking for in the hosts and hosts.allow files, and what should be changed?

As of right now, setting the ip address to what it was isn't going to be the best option for me, so I'd like to get the new one working.  It's strange, because I've had the IP address get changed before, and soon as I went around and entered it in the front-ends, everything worked fine.  Of course, that was a new IP address on the same hardware...

Thanks for the help and advice.

---

### Post by klc5555 on 2009-03-01
> **Weidbrewer said:**
> enchesss:  Could you please elaborate on what you mean by that?  There were a few things that I'd read on that, but I'm not sure what needs to be done, or how.

klc5555:  I'd need the same from you, and much more,  Everything just went right over my head.  :)

What should I be looking for in the hosts and hosts.allow files, and what should be changed?

As of right now, setting the ip address to what it was isn't going to be the best option for me, so I'd like to get the new one working.  It's strange, because I've had the IP address get changed before, and soon as I went around and entered it in the front-ends, everything worked fine.  Of course, that was a new IP address on the same hardware...

Thanks for the help and advice.

OK, a little long here. Sorry in advance.

The /etc/hosts file is very self-explanatory, once you open it up in an editor and look at it. In addition to all the commented-out explanation, there should/must be at least one active line in it --it will tell the machine  who localhost is.

127.0.0.1    localhost

In a static IP network, this server's own static IP LAN address and name (and aliases, if any) should be the next line, e.g.

10.0.2.2    mightymythserver.comcast.net    mightymythserver

Subsequent lines might include same for rest of the network machines:

10.0.2.3   punymythclient1

10.0.2.4   punymythclient2

.....etc., as necessary.  

And the file wraps up with the commented out line:

# End of hosts 

The /etc/hosts on the client machines can have a line added with the server's information, if they are unable to locate the server.

The three other "hosts.X" files in /etc are not likely to be necessary for you to edit:  hosts.allow  hosts.deny  hosts.equiv  They are set up, generally, like the hosts file itself, and in environments where extra LAN security is an issue, tell the local machine which outside machines to allow to connect, which to deny a connection to, and which outside machines are so trusted that their commands are the equivalent of the localhost.

On a static LAN, in addition to the IP addresses, you also supply a netmask (common example for class C network: 255.255.255.0) The number is shared by all machines on the same side of a LAN hub/switch, it allows the hub to determine whether a packet being sent from a local machine is to be sent to another local machine, or is to be routed to the outside.

Now when setting up static networking with the Ubuntu netorking utility on the desktop, it seems to be not uncommon to inadvertently enter in partial, incorrect, or nonsensical netmasks e.g. 255.0.0.0 (the standard for a class A network) With the wrong netmask, your server would do internet OK, but it would be invisible to the other LAN machines, and they to it. The hub couldn't tell which packages were destined locally.

To check what netmask the client machines are using, you would use the command on one of them: sudo ifconfig

And the second line of the screen output for each card eth0 (eth1, eth2...etc.) will have something like 
 inet addr:10.0.2.3  Bcast:10.0.2.255  Mask:255.255.255.0

And so if your server and your clients are on the same subnet (the same side of a hub/switch in your LAN) they will all need the same Mask value. If your newly configured server's is different, change it to the correct value in Mythbuntu's networking utility on the desktop.

Cheers! :)

---

### Post by enchesss on 2009-03-02
try commenting out the line

bind address = 127.0.0.1

in the mythtv backend server

by typing ```
sudo gedit /etc/mysql/my.cnf
``` in a terminal


here is the file on the backend:

> #
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
language	= /usr/share/mysql/english
skip-external-locking
#
# Instead of skip-networking the default is now to listen only on
# localhost which is more compatible and is not less secure.


#### front end hack to watch mythtv over network ###

#bind-address		= 127.0.0.1

#### normally the above line is NOT commented


#
# * Fine Tuning
#
key_buffer		= 16M
max_allowed_packet	= 16M
thread_stack		= 128K
thread_cache_size	= 8
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
#log		= /var/log/mysql/mysql.log
#
# Error logging goes to syslog. This is a Debian improvement :)
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
# * BerkeleyDB
#
# Using BerkeleyDB is now discouraged as its support will cease in 5.1.12.
skip-bdb
#
# * InnoDB
#
# InnoDB is enabled by default with a 10MB datafile in /var/lib/mysql/.
# Read the manual for more InnoDB related options. There are many!
# You might want to disable InnoDB to shrink the mysqld process by circa 100MB.
#skip-innodb
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
# The files must end with '.cnf', otherwise they'll be ignored.
#
!includedir /etc/mysql/conf.d/




leaving the binding in tact in the front end should still work !

here is my front end my.cnf with the binding in tact:
> #
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
language	= /usr/share/mysql/english
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
thread_stack		= 128K
thread_cache_size	= 8
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
#log		= /var/log/mysql/mysql.log
#
# Error logging goes to syslog. This is a Debian improvement :)
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
# * BerkeleyDB
#
# Using BerkeleyDB is now discouraged as its support will cease in 5.1.12.
skip-bdb
#
# * InnoDB
#
# InnoDB is enabled by default with a 10MB datafile in /var/lib/mysql/.
# Read the manual for more InnoDB related options. There are many!
# You might want to disable InnoDB to shrink the mysqld process by circa 100MB.
#skip-innodb
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
# The files must end with '.cnf', otherwise they'll be ignored.
#
!includedir /etc/mysql/conf.d/



good luck

---

### Post by Weidbrewer on 2009-03-02
Oh my dear lord...

Let me preface this post by saying this:  It is very, very possible that either A.) we're talking about two different things, or (And this is more likely) B.) I'm an idiot.

I have never had to edit this file that we're talking about, and unless something got reset/overwritten when I moved the hardware, I've been running this system for the last almost two years with this as my /etc/hosts file:

```
127.0.0.1 localhost
127.0.1.1 deus-ex

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```


That's it.  That's all of it.  What happened, what did I miss, and where did all that stuff above you two are mentioning come from?

(Again, this is not me being a smart-*** towards the two of you.  I really appreciate the help.  I've just had my brain blown square out my head, and am not sure where I fell off the trolley.

Originally, my server's IP address was 192.168.1.47.  At one point, it was changed to 192.168.1.44.  At when that happened, I just went through each of the front-ends and changed all instances of .47 to .44.  Now, the IP address is 192.168.1.33.

:-k

---

### Post by enchesss on 2009-03-02
sorry for inundating you with all of that but you asked for more specific instructions

can you post your /etc/mysql/my.cnf ?

from the backend mythtv server only please

---

### Post by tgm4883 on 2009-03-02
If you have activated the mysql service in MCC, then the bind address will be set correctly.  It will not show up that way in my.cnf though

---

### Post by klc5555 on 2009-03-02
> **Weidbrewer said:**
> Oh my dear lord...

Let me preface this post by saying this:  It is very, very possible that either A.) we're talking about two different things, or (And this is more likely) B.) I'm an idiot.

I have never had to edit this file that we're talking about, and unless something got reset/overwritten when I moved the hardware, I've been running this system for the last almost two years with this as my /etc/hosts file:

```
127.0.0.1 localhost
127.0.1.1 deus-ex

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```


That's it.  That's all of it.  What happened, what did I miss, and where did all that stuff above you two are mentioning come from?

(Again, this is not me being a smart-*** towards the two of you.  I really appreciate the help.  I've just had my brain blown square out my head, and am not sure where I fell off the trolley.

Originally, my server's IP address was 192.168.1.47.  At one point, it was changed to 192.168.1.44.  At when that happened, I just went through each of the front-ends and changed all instances of .47 to .44.  Now, the IP address is 192.168.1.33.

:-k

The difference here is that this is not a server with an IP address change. Correct? This is a new server with (I assume) a new OS and networking install and a restore of old data. And it happens to have the same name as the previous server at a different IP address. And this new server has never yet functioned correctly.

Your complaint was that the client machines could not "find the server". Not that they could not connect to the database on the server, which would imply a completely different set of problems. If the clients can contact the server, but can not connect to the database, then your problem is not simpleminded networking, and enchesss' focus on SQL issues is likely correct.

But when you have a machine on a LAN that can't be "found" by other machines on that LAN, even though its networking is clearly functioning because that machine can connect to the internet, then the problem on the LAN (barring cabling or routing with multiple hubs)is one of two: 1)incorrect/defective name resolution or hosts files on that machine or the LAN, or 2)incorrect netmask value on the new machine which has isolated the machine into its own little invisible subnet. This is pretty much Networking 101 from any time over the last 20 years.

To establish whether the clients can "find the server" or not, ping the server at a terminal from one of the clients: "ping 192.168.1.33" 

a)If the server returns the ping, then obviously the client can find it. You can also "ping deus-ex". If this ping fails, either because of "unknown host", or because ping is sending it to an old/wrong IP address, then you have a name/resolution or hosts file problem on the client. 

If the server machine's name is "deus-ex", then your /etc/hosts file on the server should include, right after the 127.x.x.x lines, the line: 

192.168.1.33  deus-ex

The /etc/hosts file on each of the client machines should include the same line 192.168.1.33  deus-ex   In the client /etc/hosts file there should be no lines putting deus-ex on any other (old or obsolete) IP address. Now, even if you have a hub on your LAN putting out defective name resolution for local addresses, it won't matter, because the machines always read from the hosts file before they look for name resolution.
.................
b) If the server is completely inaccessible to ping from the clients (and vice/versa), but you know that the server's networking is functional, because it accesses the internet, then the most likely culprit is the new server's netmask, which needs to be the same as that on the client machines. But first make sure the server can ping itself. At a terminal on the server ping 127.0.0.1 and ping localhost. The server should be able to ping itself regardless of what the netmask may be. The command: sudo ifconfig  will tell you quickly what the netmask is set to on your machines. If the server's is different from that on the established client machines, then the server's netmask should be corrected in the network utility on the desktop on your server.

.........

Ubuntu's installation always assumes a DHCP setup, and has never been particularly congenial to static IP networks. In 7.10, you could do the installation with static IP ... it just wouldn't work, period. You would have to install as DHCP, download/install the first batch of patches/updates, and then you could switch over successfully to static IP. One 7.10 installation out of every five or six for me would produce a completely blank /etc/hosts file --and the machine couldn't even find localhost until I manually edited in "127.0.0.1   localhost"

Even as recently as 8.10, you can't do an "advanced install" of a slave backend on a static IP network: no method of entering a netmask is provided in the "ping MySQL server" section  --the MySQL server ping therefore fails and the installation stops. You have to do a standard standalone install of Mythbuntu 8.10, move it from DHCP to static (with netmask) after installation, then convert the standalone to slave backend on that static IP with netmask.

So in sum one can't always rely on Ubuntu to set things up behind the scenes without intervention, particularly in static IP networking environments.

Cheers!

---

### Post by tgm4883 on 2009-03-02
On your frontends, i'd suggest using mythbuntu-log-grabber and posting the logs here.  That will help us out.

---

### Post by Weidbrewer on 2009-03-02
Okay...so, here's the deal...I just opened Myth on a frontend, just to get another look at the error screen and...it worked.  No problems, no issues, everything was fine.

So, it appears that doing the updates as I have in the past worked, and it might have been some connectivity issue.  I got nothing.


Thank you very much for your help, everyone.  On Monday, the new (permanent) hardware will be arriving and I will be moving it over...if I run in to this same issue there, I will refer back to this thread.

Again, thanks all around.

---

