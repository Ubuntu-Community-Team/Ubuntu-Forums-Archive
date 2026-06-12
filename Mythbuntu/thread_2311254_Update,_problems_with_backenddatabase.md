---
title: "Update, problems with backend/database"
date: 2016-01-25
forum: Mythbuntu
---

### Post by Senkoboy on 2016-01-25
I had mythbuntu 12.04 myth 0.25, had a few problems with some things, time to update.  I now have mythbuntu 14.04 myth 0.27.5

My backend wont start,   

```
mike@mike-desktop:~/Desktop$ mythbackend
2016-01-24 20:24:34.355482 C  mythbackend version: fixes/0.27 [v0.27.5-72-g5e18f50] www.mythtv.org
2016-01-24 20:24:34.355501 C  Qt version: compile: 4.8.6, runtime: 4.8.6
2016-01-24 20:24:34.355506 N  Enabled verbose msgs:  general
2016-01-24 20:24:34.355517 N  Setting Log Level to LOG_INFO
2016-01-24 20:24:34.366058 I  Added logging to the console
2016-01-24 20:24:34.366888 I  Setup Interrupt handler
2016-01-24 20:24:34.366901 I  Setup Terminated handler
2016-01-24 20:24:34.366912 I  Setup Segmentation fault handler
2016-01-24 20:24:34.366923 I  Setup Aborted handler
2016-01-24 20:24:34.366933 I  Setup Bus error handler
2016-01-24 20:24:34.366945 I  Setup Floating point exception handler
2016-01-24 20:24:34.366956 I  Setup Illegal instruction handler
2016-01-24 20:24:34.366969 I  Setup Real-time signal 0 handler
2016-01-24 20:24:34.367010 N  Using runtime prefix = /usr
2016-01-24 20:24:34.367025 N  Using configuration directory = /home/mike/.mythtv
2016-01-24 20:24:34.367096 I  Assumed character encoding: en_US.UTF-8
2016-01-24 20:24:34.367273 E  Error parsing: /home/mike/.mythtv/config.xml at line: 1  column: 1
2016-01-24 20:24:34.367280 E  Error Msg: unexpected end of file
2016-01-24 20:24:34.367348 E  DBHostName is not set in config.xml
2016-01-24 20:24:34.367376 E  DBHostName is not set in config.xml
2016-01-24 20:24:34.367393 N  Empty LocalHostName.
2016-01-24 20:24:34.367403 I  Using localhost value of mike-desktop
2016-01-24 20:24:34.379834 E  Unable to connect to database!
2016-01-24 20:24:34.379857 E  Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

2016-01-24 20:24:34.379885 I  UPNP Search 2 secs
2016-01-24 20:24:34.380006 E  Error parsing: /home/mike/.mythtv/config.xml at line: 1  column: 1
2016-01-24 20:24:34.380013 E  Error Msg: unexpected end of file
2016-01-24 20:24:34.467779 I  New Client:  (#1)
2016-01-24 20:24:34.757848 I  UPNP Search 1 secs
2016-01-24 20:24:35.193429 I  UPNP Search 1 secs

No UPnP backends found

Would you like to configure the database connection now? [no]  2016-01-24 20:24:36.520191 I  No UPnP backends found

```
If I try  "sudo status mysql"
I get "mysql start/running, process 1315"

There were some errors during the upgrade.  Not sure what I should try next.

Also, at home/mike/mythtv/config.xml I have:

XML Parsing Error: no element found
Location: file:///home/mike/.mythtv/config.xml
Line Number 1, Column 1:

---

### Post by tgm4883 on 2016-01-25
> **Senkoboy said:**
> I had mythbuntu 12.04 myth 0.25, had a few problems with some things, time to update.  I now have mythbuntu 14.04 myth 0.27.5

My backend wont start,   

```
mike@mike-desktop:~/Desktop$ mythbackend
2016-01-24 20:24:34.355482 C  mythbackend version: fixes/0.27 [v0.27.5-72-g5e18f50] www.mythtv.org
2016-01-24 20:24:34.355501 C  Qt version: compile: 4.8.6, runtime: 4.8.6
2016-01-24 20:24:34.355506 N  Enabled verbose msgs:  general
2016-01-24 20:24:34.355517 N  Setting Log Level to LOG_INFO
2016-01-24 20:24:34.366058 I  Added logging to the console
2016-01-24 20:24:34.366888 I  Setup Interrupt handler
2016-01-24 20:24:34.366901 I  Setup Terminated handler
2016-01-24 20:24:34.366912 I  Setup Segmentation fault handler
2016-01-24 20:24:34.366923 I  Setup Aborted handler
2016-01-24 20:24:34.366933 I  Setup Bus error handler
2016-01-24 20:24:34.366945 I  Setup Floating point exception handler
2016-01-24 20:24:34.366956 I  Setup Illegal instruction handler
2016-01-24 20:24:34.366969 I  Setup Real-time signal 0 handler
2016-01-24 20:24:34.367010 N  Using runtime prefix = /usr
2016-01-24 20:24:34.367025 N  Using configuration directory = /home/mike/.mythtv
2016-01-24 20:24:34.367096 I  Assumed character encoding: en_US.UTF-8
2016-01-24 20:24:34.367273 E  Error parsing: /home/mike/.mythtv/config.xml at line: 1  column: 1
2016-01-24 20:24:34.367280 E  Error Msg: unexpected end of file
2016-01-24 20:24:34.367348 E  DBHostName is not set in config.xml
2016-01-24 20:24:34.367376 E  DBHostName is not set in config.xml
2016-01-24 20:24:34.367393 N  Empty LocalHostName.
2016-01-24 20:24:34.367403 I  Using localhost value of mike-desktop
2016-01-24 20:24:34.379834 E  Unable to connect to database!
2016-01-24 20:24:34.379857 E  Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

2016-01-24 20:24:34.379885 I  UPNP Search 2 secs
2016-01-24 20:24:34.380006 E  Error parsing: /home/mike/.mythtv/config.xml at line: 1  column: 1
2016-01-24 20:24:34.380013 E  Error Msg: unexpected end of file
2016-01-24 20:24:34.467779 I  New Client:  (#1)
2016-01-24 20:24:34.757848 I  UPNP Search 1 secs
2016-01-24 20:24:35.193429 I  UPNP Search 1 secs

No UPnP backends found

Would you like to configure the database connection now? [no]  2016-01-24 20:24:36.520191 I  No UPnP backends found

```
If I try  "sudo status mysql"
I get "mysql start/running, process 1315"

There were some errors during the upgrade.  Not sure what I should try next.

Also, at home/mike/mythtv/config.xml I have:

XML Parsing Error: no element found
Location: file:///home/mike/.mythtv/config.xml
Line Number 1, Column 1:

Errors are generally something to pay attention to. Not knowing what they are, I can at least tell you that mythtv changed from using mysql.txt to config.xml at 0.26, and thus you need to pull the correct info from your mysql.txt file (in the same directory as config.xml) and then make your XML file look similiar to

```
<Configuration>
  <LocalHostName>my-unique-identifier-goes-here</LocalHostName>
  <Database>
    <PingHost>1</PingHost>
    <Host>BACKENDIP</Host>
    <UserName>mythtv</UserName>
    <Password>PASSWORDHERE</Password>
    <DatabaseName>mythconverg</DatabaseName>
    <Port>3306</Port>
  </Database>
  <WakeOnLAN>
    <Enabled>0</Enabled>
    <SQLReconnectWaitTime>0</SQLReconnectWaitTime>
    <SQLConnectRetry>5</SQLConnectRetry>
    <Command>echo 'WOLsqlServerCommand not set'</Command>
  </WakeOnLAN>
  <UPnP>
    <UDN>
      <MediaRenderer></MediaRenderer>
    </UDN>
  </UPnP>
</Configuration>
```

---

### Post by Senkoboy on 2016-01-27
My mysql.txt shows:  

```
DBHostName=localhost

# By default, Myth tries to ping the DB host to see if it exists.
# If your DB host or network doesn't accept pings, set this to no:
#
#DBHostPing=no

DBPort=3306
DBUserName=mythtv
DBPassword=wh0GzEdP
DBName=mythconverg
DBType=QMYSQL

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
```

When I ran $ mythbackend and said yes to : Would you like to configure the database connection now? this is what I got.

```
Would you like to configure the database connection now? [no]  2016-01-27 16:53:01.282301 I  No UPnP backends found
yes
Database host name:  localhost
Should I test connectivity to this host using the ping command? [yes]  n
Database non-default port: [3306]  
Database name: [mythconverg]  
Database user name: [mythtv]  
Database password: [mythtv]  wh0GzEdP
Unique identifier for this machine (if empty, the local host name will be used): [my-unique-identifier-goes-here]  
Would you like to use Wake-On-LAN to retry database connections? [no]  
2016-01-27 16:54:54.849109 N  Setting QT default locale to en_US
2016-01-27 16:54:54.849197 I  Current locale en_US
2016-01-27 16:54:54.849254 N  Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2016-01-27 16:54:54.856514 E  MySQL time zone support is missing.  Please install it and try again.  See 'mysql_tzinfo_to_sql' for assistance.

```

If I can get the time zone support fixed maybe it will work.  Am I on the right track?

Thanks

---

### Post by aelfric55 on 2016-01-28
[https://www.mythtv.org/wiki/MySQL_Time_Zone_Tables](https://www.mythtv.org/wiki/MySQL_Time_Zone_Tables)

Takes maybe 5 minutes to set up.

But the first time mythbackend is started after this, it will take one heck of a long time to upgrade every entry in your 0.25 vintage mythconverg from local time to UTC. From over 20 minutes to something on the order of 2 hours, depending on size of database. It may seem that a process has hung, but it just needs a lot of time to finish.

---

### Post by Senkoboy on 2016-01-29
Between editing the XML file with gedit and messing with the time zone problems I have life.  I still have some things that don't work quite right, but they didn't work quite right before the upgrade either.  I can watch and recorded now.  I will try to get more information on my other problems and make a new post on them later.

If you ever wonder how important your mythtv box is, break it for a week........:D 

Thanks all

---

