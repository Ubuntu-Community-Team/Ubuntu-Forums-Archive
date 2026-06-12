---
title: "MythTV Help"
date: 2008-10-14
forum: Mythbuntu
---

### Post by 4t0m1c_w07f on 2008-10-14
Hi
I recently bought a random tv card with a philips SAA713x PCI TV chip set.
I then installed mythtv and when I run the mythtv-frontend from the menu, I start the database login sequence. I filled in the details and instead of using the login and password that was supplied, I used the one i use for my user. I clicked next and then finish and it said it cannot login to database.

Please help me

---

### Post by Sef on 2008-10-14
Moved to Mythbuntu forum.

---

### Post by klc5555 on 2008-10-14
> **4t0m1c_w07f said:**
> Hi
I recently bought a random tv card with a philips SAA713x PCI TV chip set.
I then installed mythtv and when I run the mythtv-frontend from the menu, I start the database login sequence. I filled in the details and instead of using the login and password that was supplied, I used the one i use for my user. I clicked next and then finish and it said it cannot login to database.

Please help me

Shortest, easiest answer: In the mythtv-frontend setup, put back the login/password combo that it originally had. 

The database login info that is editable in the frontend is for the situation that you might be using this frontend to connect to some other, remote backend somewhere that was already set up; you would edit this frontend's database login information to match that previously set-up backend. Your mysql database on your machine (which is owned by the mythtv backend)is still waiting for that original supplied login and password that it gave you.

You say you don't have that original login/password any more? You can set the mysql password to whatever you want by following this mini-howto:
[http://community.zikula.org/Article1273.htm](http://community.zikula.org/Article1273.htm)
or other similar how-tos.

You can also back up your mysql database (if there was actually any data in it yet), then "completely uninstall" mysql server via synaptic and reinstall (gives you a clean slate). Then restore your database. As described in the first few postings of this thread from the mythtv list at Gossamer Threads:

[http://www.gossamer-threads.com/lists/mythtv/users/265008](http://www.gossamer-threads.com/lists/mythtv/users/265008)

Good luck! :)

---

### Post by 4t0m1c_w07f on 2008-10-14
> **klc5555 said:**
> Shortest, easiest answer: In the mythtv-frontend setup, put back the login/password combo that it originally had. 

The database login info that is editable in the frontend is for the situation that you might be using this frontend to connect to some other, remote backend somewhere that was already set up; you would edit this frontend's database login information to match that previously set-up backend. Your mysql database on your machine (which is owned by the mythtv backend)is still waiting for that original supplied login and password that it gave you.

You say you don't have that original login/password any more? You can set the mysql password to whatever you want by following this mini-howto:
[http://community.zikula.org/Article1273.htm](http://community.zikula.org/Article1273.htm)
or other similar how-tos.

You can also back up your mysql database (if there was actually any data in it yet), then "completely uninstall" mysql server via synaptic and reinstall (gives you a clean slate). Then restore your database. As described in the first few postings of this thread from the mythtv list at Gossamer Threads:

[http://www.gossamer-threads.com/lists/mythtv/users/265008](http://www.gossamer-threads.com/lists/mythtv/users/265008)

Good luck! :)

I tried the first 2 commands of the mini howto and got this:

```
jared@4t0m1c_w07f:~$ kill `cat /var/lib/mysql/hostname.pid`
cat: /var/lib/mysql/hostname.pid: No such file or directory
kill: usage: kill [-s sigspec | -n signum | -sigspec] pid | jobspec ... or kill -l [sigspec]
jared@4t0m1c_w07f:~$ kill cat /var/lib/mysql/hostname.pid
bash: kill: cat: arguments must be process or job IDs
bash: kill: /var/lib/mysql/hostname.pid: arguments must be process or job IDs
jared@4t0m1c_w07f:~$ /usr/bin/safe_mysqld --skip-grant-tables& 
[1] 20041
jared@4t0m1c_w07f:~$ bash: /usr/bin/safe_mysqld: No such file or directory

```

---

### Post by issih on 2008-10-14
Open the file:

/etc/mythtv/mysql.txt

in a text browser. At the top of that file are the fields DBUserName, DBPassword and DBDatabasename. Use these values in the database login screen for myth tv's front end and all should be well.

Hope that helps

---

### Post by 4t0m1c_w07f on 2008-10-14
> **issih said:**
> Open the file:

/etc/mythtv/mysql.txt

in a text browser. At the top of that file are the fields DBUserName, DBPassword and DBDatabasename. Use these values in the database login screen for myth tv's front end and all should be well.

Hope that helps

This is the contents of the file:

> DBHostName=localhost

# By default, Myth tries to ping the DB host to see if it exists.
# If your DB host or network doesn't accept pings, set this to no:
#
DBHostPing=no

DBUserName=root
DBPassword=l1nuxboi
DBName=mythtv
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

This is all the information that I used when  I launched the frontend and filled in this info... After that it just says that I cannot login to datbase.

---

### Post by 4t0m1c_w07f on 2008-10-14
> **issih said:**
> Open the file:

/etc/mythtv/mysql.txt

in a text browser. At the top of that file are the fields DBUserName, DBPassword and DBDatabasename. Use these values in the database login screen for myth tv's front end and all should be well.

Hope that helps

This is the contents of the file:

> DBHostName=localhost

# By default, Myth tries to ping the DB host to see if it exists.
# If your DB host or network doesn't accept pings, set this to no:
#
DBHostPing=no

DBUserName=root
DBPassword=l1nuxboi
DBName=mythtv
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

This is all the information that I used when  I launched the frontend and filled in this info... After that it just says that I cannot login to database.

---

### Post by issih on 2008-10-14
I'm pretty sure you have things a bit screwed up here. The normal way to get this set up (e.g. by using the mythbuntu control centre) is as follows.

The database is called something like mythconverg.
The database user is a group called mythtv.

All actual users of the system who want to use mythtv must then belong to the mythtv group.

Because you have root owning your database, your users can't be part of the appropriate group.

Probably easiest to start again and reinstall. I'd recommend installing the mythbuntu control centre package, as it takes a fair amount of the pain out of the process.

Hope that helps

---

