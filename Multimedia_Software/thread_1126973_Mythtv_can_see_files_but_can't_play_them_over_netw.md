---
title: "Mythtv can see files but can't play them over network"
date: 2009-04-15
forum: Multimedia Software
---

### Post by Captain_Glen on 2009-04-15
Hi,

I have two ubuntu machines: 192.168.0.6 with Hardy Heron and my mythtv backend and 192.168.0.2 with Intrepid Ibex and my mythtv frontend.

This is the contents of my mysql.txt on the front end:
```
# By default, Myth tries to ping the DB host to see if it exists.
# If your DB host or network doesn't accept pings, set this to no:
#
DBHostPing=no
DBHostName=192.168.0.6
DBUserName=mythtv
DBPassword=mythtv
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
```

When I run the front end on 192.168.0.2 It loads up fine.  But when I click watch tv nothing happens.  When I go to watch recordings it shows a list of the recordings.  But when I try to play one it gives an error: the file for this recording can not be found.

---

### Post by jcanderson01 on 2009-05-27
I was having the same problem until I made sure both the front end and back end were set to the same time zone. Once I did that, I was able to play the videos on the front end with no problems.

---

