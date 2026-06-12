---
title: "Could not connect to the master backend server"
date: 2010-10-28
forum: Mythbuntu
---

### Post by phroman on 2010-10-28
Hello all, I know many people have seen this before, I encountered it last year, but it was fixed with an update at some point, I didn't find the cause/fix.

  I'm getting this error on startup now:

Could not connect to the master backend server -- is it running.
Is the IP address set for it in the setup program correct?

If I restart Mythbackend and then restart Mythfrontend, things work.  I've come across something about udev and about something getting loaded before the frontend but it was beyond my expertise. (or lack thereof)  Is this likely, one service starting before another and that's breaking something?   

I've seen this error in posts before but I could never get the solutions to work for me at the time.  Here's some info:


In Mythfrontend > Set Up > General > Database Configuration -  I've set the database IP to 127.0.0.1  The Port number is not set by default. The database name, username and password are all correct.

In Mythbackend > General > Host Address Backend Setup - I've got the IP set as 127.0.0.1 in Local Backend and Master Backend, port numbers are default.  


Here is my /etc/hosts file:

```

192.168.1.5	mythserver	# Added by NetworkManager
127.0.0.1	localhost.localdomain	localhost
::1	mythserver	localhost6.localdomain6	localhost6
127.0.1.1	mythserver

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

And /etc/mythtv/mysql.txt

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
DBPassword=fRt7YqPe

```

I deleted the ~/.mythtv/mysql.txt file as indicated in another post but it was re-created at the next boot by the filecreator gini...


If there's anything else I can provide please let me know and thank you mucho
 for any help.  Thanks!

---

### Post by tgm4883 on 2010-10-28
The frontend is likely starting before the backend/database. What is the output of 

```
dpkg -l mythtv-frontend mythtv-backend
```

---

### Post by phroman on 2010-10-28
Hey, thanks for replying, here's the output.

```
joe@mythserver:~/Desktop$ dpkg -l mythtv-frontend mythtv-backend
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  mythtv-backend 0.23.1+fixes26 A personal video recorder application (serve
ii  mythtv-fronten 0.23.1+fixes26 A personal video recorder application (clien
joe@mythserver:~/Desktop$ 
```

---

### Post by thatguruguy on 2010-10-28
I get that message just about every time I re-boot the computer.  My super-technical method of dealing with the issue is to do nothing.  After a minute or two, the backend and the frontend finally synch up on their own.

---

