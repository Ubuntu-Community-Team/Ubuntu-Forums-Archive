---
title: "Myth backend not starting on boot up after upgrade to 0.25"
date: 2012-04-16
forum: Mythbuntu
---

### Post by Paulgirardin on 2012-04-16
I have been advised that it may have something to do with my mythtv-backend.conf
On this page is an example of what mythtv-backend.conf should look like:
[http://www.mythtv.org/wiki/Upstart_mythbackend_Configuration](http://www.mythtv.org/wiki/Upstart_mythbackend_Configuration)

My version looks quite different:

```
# MythTV Backend service

description     "MythTV Backend"
author          "Mario Limonciello <superm1@ubuntu.com>"

start on (local-filesystems and net-device-up IFACE!=lo and started udev-finish)
stop on runlevel [016]

#expect fork
respawn
respawn limit 2 3600

pre-start script 
    [ -x /usr/sbin/mysqld ] || exit 0
    for i in `seq 1 30` ; do
       /usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping && exit 0
       sleep .5
    done
end script

script
	test -f /etc/default/locale && . /etc/default/locale || true
	LANG=$LANG /usr/bin/mythbackend --syslog local7 --user mythtv
end script
```

I'm not sure how I should change this.

Any suggestions?

---

### Post by Paulgirardin on 2012-04-16
I've tried 2 versions of the new file - neither work

```
[/# MythTV Backend service

description     "MythTV Backend"
author          "Mario Limonciello <superm1@ubuntu.com>"

start on (local-filesystems and net-device-up IFACE!=lo and started udev-finish)
stop on starting shutdown

#expect fork
respawn

script
        ulimit -c unlimited                              
        . /etc/default/locale                            
        export LANG
        export LC_ALL=$LANG
        ARGS="--syslog local7"                           
        sleep 5                                         
        test -f /etc/default/mythtv-backend && . /etc/default/mythtv-backend || true
        /usr/bin/mythbackend --user mythtv $ARGS $EXTRA_ARGS
end script
```

And

```
# MythTV Backend service

description     "MythTV Backend"
author          "Mario Limonciello <superm1@ubuntu.com>"

start on (local-filesystems and net-device-up IFACE!=lo and started udev-finish)
stop on starting shutdown

#expect fork
respawn

script
        ulimit -c unlimited                              
        . /etc/default/locale                            
        export LANG
        export LC_ALL=$LANG
        ARGS="--logfile /var/log/mythtv/mythbackend.log" #
        ARGS="--logpath /var/log/mythtv"                 # Note 3. (choose 1)
        ARGS="--syslog local7"                           
        sleep 5                                         
        test -f /etc/default/mythtv-backend && . /etc/default/mythtv-backend || true
        /usr/bin/mythbackend --user mythtv $ARGS $EXTRA_ARGS
end script
```

---

### Post by tgm4883 on 2012-04-16
> **Paulgirardin said:**
> I've tried 2 versions of the new file - neither work

```
[/# MythTV Backend service

description     "MythTV Backend"
author          "Mario Limonciello <superm1@ubuntu.com>"

start on (local-filesystems and net-device-up IFACE!=lo and started udev-finish)
stop on starting shutdown

#expect fork
respawn

script
        ulimit -c unlimited                              
        . /etc/default/locale                            
        export LANG
        export LC_ALL=$LANG
        ARGS="--syslog local7"                           
        sleep 5                                         
        test -f /etc/default/mythtv-backend && . /etc/default/mythtv-backend || true
        /usr/bin/mythbackend --user mythtv $ARGS $EXTRA_ARGS
end script
```

And

```
# MythTV Backend service

description     "MythTV Backend"
author          "Mario Limonciello <superm1@ubuntu.com>"

start on (local-filesystems and net-device-up IFACE!=lo and started udev-finish)
stop on starting shutdown

#expect fork
respawn

script
        ulimit -c unlimited                              
        . /etc/default/locale                            
        export LANG
        export LC_ALL=$LANG
        ARGS="--logfile /var/log/mythtv/mythbackend.log" #
        ARGS="--logpath /var/log/mythtv"                 # Note 3. (choose 1)
        ARGS="--syslog local7"                           
        sleep 5                                         
        test -f /etc/default/mythtv-backend && . /etc/default/mythtv-backend || true
        /usr/bin/mythbackend --user mythtv $ARGS $EXTRA_ARGS
end script
```

Try changing

```
IFACE!=lo
```

to 

```
IFACE==eth0
```

---

### Post by Paulgirardin on 2012-04-16
Will that be applicable on a combined BE/FE system?

The original file was IFACE!=lo

---

### Post by Paulgirardin on 2012-04-16
IFACE==eth0 does not fix the problem

---

### Post by tgm4883 on 2012-04-16
> **Paulgirardin said:**
> IFACE==eth0 does not fix the problem

Correction, make that

```
IFACE=eth0
```

---

### Post by Paulgirardin on 2012-04-16
sorry no luck

---

### Post by tgm4883 on 2012-04-16
> **Paulgirardin said:**
> sorry no luck

If you look in the backend log right after boot (before starting it), do you see it attempting to start and perhaps saying why it cannot?

---

### Post by Paulgirardin on 2012-04-16
Heres' the most recent entries in mythbackend.log:

```
 Apr 17 02:11:32 myth mythbackend[1802]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: myth as a client (events: 1)
Apr 17 02:11:36 myth mythbackend[1802]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Apr 17 02:11:36 myth mythbackend[1802]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: myth as a client (events: 0)
Apr 17 02:11:36 myth mythbackend[1802]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Apr 17 02:11:36 myth mythbackend[1802]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: myth as a client (events: 1)
Apr 17 07:42:36 myth mythbackend[2187]: C thread_unknown mythcommandlineparser.cpp:2534 (ConfigureLogging) mythbackend version: fixes/0.25 [v0.25-9-gefada3f] www.mythtv.org
Apr 17 07:42:36 myth mythbackend[2187]: N thread_unknown mythcommandlineparser.cpp:2536 (ConfigureLogging) Enabled verbose msgs:  general
Apr 17 07:42:36 myth mythbackend[2187]: N thread_unknown logging.cpp:1176 (logStart) Setting Log Level to LOG_INFO
Apr 17 07:42:36 myth mythbackend[2187]: I thread_unknown logging.cpp:229 (FileLogger) Added logging to the console
Apr 17 07:42:36 myth mythbackend[2187]: I thread_unknown logging.cpp:369 (SyslogLogger) Added syslogging to facility local7
Apr 17 07:42:36 myth mythbackend[2187]: I thread_unknown logging.cpp:425 (DatabaseLogger) Added database logging to table logging
Apr 17 07:42:36 myth mythbackend[2187]: N thread_unknown logging.cpp:1215 (logStart) Setting up SIGHUP handler
Apr 17 07:42:36 myth mythbackend[2187]: N thread_unknown mythdirs.cpp:51 (InitializeMythDirs) Using runtime prefix = /usr
Apr 17 07:42:36 myth mythbackend[2187]: N thread_unknown mythdirs.cpp:64 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Apr 17 07:42:36 myth mythbackend[2187]: I CoreContext mythcorecontext.cpp:227 (Init) Assumed character encoding: en_NZ.UTF-8
Apr 17 07:42:36 myth mythbackend[2187]: N CoreContext mythcontext.cpp:477 (LoadDatabaseSettings) Empty LocalHostName.
Apr 17 07:42:36 myth mythbackend[2187]: I CoreContext mythcontext.cpp:481 (LoadDatabaseSettings) Using localhost value of myth
Apr 17 07:42:36 myth mythbackend[2187]: N CoreContext mythcorecontext.cpp:1270 (InitLocale) Setting QT default locale to en_NZ
Apr 17 07:42:36 myth mythbackend[2187]: I CoreContext mythcorecontext.cpp:1303 (SaveLocaleDefaults) Current locale en_NZ
Apr 17 07:42:36 myth mythbackend[2187]: E CoreContext mythlocale.cpp:108 (LoadDefaultsFromXML) No locale defaults file for en_NZ, skipping
Apr 17 07:42:36 myth mythbackend[2187]: I CoreContext schemawizard.cpp:117 (Compare) Current MythTV Schema Version (DBSchemaVer): 1299
Apr 17 07:42:36 myth mythbackend[2187]: I CoreContext mythtranslation.cpp:66 (load) Loading en_gb translation for module mythfrontend
Apr 17 07:42:36 myth mythbackend[2187]: N CoreContext main_helpers.cpp:556 (run_backend) MythBackend: Starting up as the master server.
Apr 17 07:42:39 myth mythbackend[2187]: I CoreContext programinfo.cpp:2052 (CheckProgramIDAuthorities) Found 2 distinct programid authorities
Apr 17 07:42:39 myth mythbackend[2187]: I Scheduler mythdbcon.cpp:422 (getStaticCon) New static DB connectionSchedCon
Apr 17 07:42:39 myth mythbackend[2187]: I CoreContext serverpool.cpp:306 (listen) Listening on TCP 127.0.0.1:6544
Apr 17 07:42:39 myth mythbackend[2187]: I CoreContext serverpool.cpp:306 (listen) Listening on TCP [0:0:0:0:0:0:0:1]:6544
Apr 17 07:42:39 myth mythbackend[2187]: N CoreContext mediaserver.cpp:169 (Init) MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
Apr 17 07:42:39 myth mythbackend[2187]: I CoreContext main_helpers.cpp:626 (run_backend) Main::Registering HttpStatus Extension
Apr 17 07:42:39 myth mythbackend[2187]: I CoreContext serverpool.cpp:306 (listen) Listening on TCP 127.0.0.1:6543
Apr 17 07:42:39 myth mythbackend[2187]: I CoreContext serverpool.cpp:306 (listen) Listening on TCP [0:0:0:0:0:0:0:1]:6543
Apr 17 07:42:39 myth mythbackend[2187]: N CoreContext autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
Apr 17 07:42:42 myth mythbackend[2187]: I Scheduler scheduler.cpp:2010 (HandleReschedule) Reschedule requested for id -1.
Apr 17 07:42:42 myth mythbackend[2187]: I Scheduler scheduler.cpp:2068 (HandleReschedule) Scheduled 2 items in 0.1 = 0.01 match + 0.13 place
Apr 17 07:42:42 myth mythbackend[2187]: I Scheduler scheduler.cpp:2135 (HandleRunSchedulerStartup) Scheduler: Seem to be woken up by USER
Apr 17 07:42:49 myth mythbackend[2187]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Apr 17 07:42:49 myth mythbackend[2187]: I HouseKeeping housekeeper.cpp:299 (RunHouseKeeping) Running mythfilldatabase
Apr 17 07:42:49 myth mythbackend[2187]: I SystemIOHandlerW system-unix.cpp:90 (run) Starting IO manager (write)
Apr 17 07:42:49 myth mythbackend[2187]: I SystemIOHandlerR system-unix.cpp:90 (run) Starting IO manager (read)
Apr 17 07:42:49 myth mythbackend[2187]: I SystemSignalManager system-unix.cpp:485 (run) Starting process signal handler
Apr 17 07:42:49 myth mythbackend[2187]: I SystemManager system-unix.cpp:263 (run) Starting process manager
Apr 17 07:42:52 myth mythbackend[2187]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Apr 17 07:42:52 myth mythbackend[2187]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: myth as a client (events: 0)
Apr 17 07:42:52 myth mythbackend[2187]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Apr 17 07:42:52 myth mythbackend[2187]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: myth as a client (events: 1)
Apr 17 07:42:52 myth mythbackend[2187]: I Scheduler scheduler.cpp:2010 (HandleReschedule) Reschedule requested for id -1.
Apr 17 07:42:52 myth mythbackend[2187]: I Scheduler scheduler.cpp:2068 (HandleReschedule) Scheduled 2 items in 0.1 = 0.01 match + 0.10 place
Apr 17 07:43:21 myth mythbackend[2187]: N CoreContext main_helpers.cpp:664 (run_backend) MythBackend exiting
Apr 17 07:43:21 myth mythbackend[2187]: E CoreContext mmulticastsocketdevice.cpp:62 (MMulticastSocketDevice) MMulticastSocketDevice(239.255.255.250:25): setsockopt - IP_ADD_MEMBERSHIP #012#011#011#011eno: No such device (19)
Apr 17 07:43:21 myth mythbackend[2187]: I CoreContext mythcontext.cpp:1115 (~MythContext) Waiting for threads to exit
```

---

### Post by Paulgirardin on 2012-04-17
bump

---

### Post by Paulgirardin on 2012-04-17
here's another section out of mythbackend.log:

```
Apr 17 17:24:24 myth mythbackend[1822]: N thread_unknown mythcommandlineparser.cpp:2536 (ConfigureLogging) Enabled verbose msgs:  general
Apr 17 17:24:24 myth mythbackend[1822]: N thread_unknown logging.cpp:1176 (logStart) Setting Log Level to LOG_INFO
Apr 17 17:24:24 myth mythbackend[1822]: I thread_unknown logging.cpp:229 (FileLogger) Added logging to the console
Apr 17 17:24:24 myth mythbackend[1822]: I thread_unknown logging.cpp:369 (SyslogLogger) Added syslogging to facility local7
Apr 17 17:24:24 myth mythbackend[1822]: I thread_unknown logging.cpp:425 (DatabaseLogger) Added database logging to table logging
Apr 17 17:24:24 myth mythbackend[1822]: N thread_unknown logging.cpp:1215 (logStart) Setting up SIGHUP handler
Apr 17 17:24:24 myth mythbackend[1822]: N thread_unknown mythdirs.cpp:51 (InitializeMythDirs) Using runtime prefix = /usr
Apr 17 17:24:24 myth mythbackend[1822]: N thread_unknown mythdirs.cpp:64 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Apr 17 17:24:24 myth mythbackend[1822]: I CoreContext mythcorecontext.cpp:227 (Init) Assumed character encoding: en_NZ.UTF-8
Apr 17 17:24:24 myth mythbackend[1822]: N CoreContext mythcontext.cpp:477 (LoadDatabaseSettings) Empty LocalHostName.
Apr 17 17:24:24 myth mythbackend[1822]: I CoreContext mythcontext.cpp:481 (LoadDatabaseSettings) Using localhost value of myth
Apr 17 17:24:24 myth mythbackend[1822]: N CoreContext mythcorecontext.cpp:1270 (InitLocale) Setting QT default locale to en_NZ
Apr 17 17:24:24 myth mythbackend[1822]: I CoreContext mythcorecontext.cpp:1303 (SaveLocaleDefaults) Current locale en_NZ
Apr 17 17:24:24 myth mythbackend[1822]: E CoreContext mythlocale.cpp:108 (LoadDefaultsFromXML) No locale defaults file for en_NZ, skipping
Apr 17 17:24:24 myth mythbackend[1822]: I CoreContext schemawizard.cpp:117 (Compare) Current MythTV Schema Version (DBSchemaVer): 1299
Apr 17 17:24:24 myth mythbackend[1822]: I CoreContext mythtranslation.cpp:66 (load) Loading en_gb translation for module mythfrontend
Apr 17 17:24:24 myth mythbackend[1822]: N CoreContext main_helpers.cpp:556 (run_backend) MythBackend: Starting up as the master server.
Apr 17 17:24:28 myth mythbackend[1822]: I CoreContext programinfo.cpp:2052 (CheckProgramIDAuthorities) Found 2 distinct programid authorities
Apr 17 17:24:28 myth mythbackend[1822]: I Scheduler mythdbcon.cpp:422 (getStaticCon) New static DB connectionSchedCon
Apr 17 17:24:28 myth mythbackend[1822]: I CoreContext serverpool.cpp:306 (listen) Listening on TCP 127.0.0.1:6544
Apr 17 17:24:28 myth mythbackend[1822]: I CoreContext serverpool.cpp:306 (listen) Listening on TCP [0:0:0:0:0:0:0:1]:6544
Apr 17 17:24:28 myth mythbackend[1822]: N CoreContext mediaserver.cpp:169 (Init) MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
Apr 17 17:24:28 myth mythbackend[1822]: I CoreContext main_helpers.cpp:626 (run_backend) Main::Registering HttpStatus Extension
Apr 17 17:24:28 myth mythbackend[1822]: I CoreContext serverpool.cpp:306 (listen) Listening on TCP 127.0.0.1:6543
Apr 17 17:24:28 myth mythbackend[1822]: I CoreContext serverpool.cpp:306 (listen) Listening on TCP [0:0:0:0:0:0:0:1]:6543
Apr 17 17:24:28 myth mythbackend[1822]: N CoreContext autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
Apr 17 17:24:31 myth mythbackend[1822]: I Scheduler scheduler.cpp:2010 (HandleReschedule) Reschedule requested for id -1.
Apr 17 17:24:31 myth mythbackend[1822]: I Scheduler scheduler.cpp:2068 (HandleReschedule) Scheduled 2 items in 0.2 = 0.06 match + 0.19 place
Apr 17 17:24:31 myth mythbackend[1822]: I Scheduler scheduler.cpp:2135 (HandleRunSchedulerStartup) Scheduler: Seem to be woken up by USER
Apr 17 17:24:37 myth mythbackend[1822]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Apr 17 17:24:37 myth mythbackend[1822]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: myth as a client (events: 0)
Apr 17 17:24:37 myth mythbackend[1822]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Apr 17 17:24:37 myth mythbackend[1822]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: myth as a client (events: 1)
Apr 17 17:24:38 myth mythbackend[1822]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Apr 17 17:25:47 myth mythbackend[1822]: N Expire autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
Apr 17 17:28:31 myth mythbackend[1822]: I SystemIOHandlerW system-unix.cpp:90 (run) Starting IO manager (write)
Apr 17 17:28:31 myth mythbackend[1822]: I SystemIOHandlerR system-unix.cpp:90 (run) Starting IO manager (read)
Apr 17 17:28:31 myth mythbackend[1822]: I SystemSignalManager system-unix.cpp:485 (run) Starting process signal handler
Apr 17 17:28:31 myth mythbackend[1822]: I SystemManager system-unix.cpp:263 (run) Starting process manager
Apr 17 17:28:31 myth mythbackend[1822]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Apr 17 17:28:31 myth mythbackend[1822]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: myth as a client (events: 0)
Apr 17 17:28:31 myth mythbackend[1822]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Apr 17 17:28:31 myth mythbackend[1822]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: myth as a client (events: 1)
Apr 17 17:28:44 myth mythbackend[1822]: I Scheduler scheduler.cpp:2010 (HandleReschedule) Reschedule requested for id 778.
Apr 17 17:28:44 myth mythbackend[1822]: I Scheduler scheduler.cpp:2068 (HandleReschedule) Scheduled 3 items in 0.1 = 0.01 match + 0.12 place
Apr 17 17:28:46 myth mythbackend[1822]: I Scheduler scheduler.cpp:2010 (HandleReschedule) Reschedule requested for id 779.
Apr 17 17:28:46 myth mythbackend[1822]: I Scheduler scheduler.cpp:2068 (HandleReschedule) Scheduled 4 items in 0.1 = 0.01 match + 0.13 place
Apr 17 17:28:53 myth mythbackend[1822]: I Scheduler scheduler.cpp:2010 (HandleReschedule) Reschedule requested for id 780.
Apr 17 17:28:53 myth mythbackend[1822]: I Scheduler scheduler.cpp:2068 (HandleReschedule) Scheduled 5 items in 0.1 = 0.01 match + 0.11 place
Apr 17 17:29:02 myth mythbackend[1822]: I Scheduler scheduler.cpp:2010 (HandleReschedule) Reschedule requested for id 781.
Apr 17 17:29:02 myth mythbackend[1822]: I Scheduler scheduler.cpp:2068 (HandleReschedule) Scheduled 6 items in 0.1 = 0.00 match + 0.09 place
Apr 17 17:29:08 myth mythbackend[1822]: I Scheduler scheduler.cpp:2010 (HandleReschedule) Reschedule requested for id 782.
Apr 17 17:29:08 myth mythbackend[1822]: I Scheduler scheduler.cpp:2068 (HandleReschedule) Scheduled 7 items in 0.1 = 0.00 match + 0.11 place
Apr 17 17:29:14 myth mythbackend[1822]: I Scheduler scheduler.cpp:2010 (HandleReschedule) Reschedule requested for id 783.
Apr 17 17:29:15 myth mythbackend[1822]: I Scheduler scheduler.cpp:2068 (HandleReschedule) Scheduled 8 items in 0.1 = 0.00 match + 0.12 place
Apr 17 17:29:17 myth mythbackend[1822]: I Scheduler scheduler.cpp:2010 (HandleReschedule) Reschedule requested for id 784.
Apr 17 17:29:17 myth mythbackend[1822]: I Scheduler scheduler.cpp:2068 (HandleReschedule) Scheduled 9 items in 0.1 = 0.00 match + 0.11 place
Apr 17 17:29:26 myth mythbackend[1822]: I Scheduler scheduler.cpp:2010 (HandleReschedule) Reschedule requested for id 785.
Apr 17 17:29:26 myth mythbackend[1822]: I Scheduler scheduler.cpp:2068 (HandleReschedule) Scheduled 10 items in 0.1 = 0.01 match + 0.09 place
Apr 17 17:29:33 myth mythbackend[1822]: I Scheduler scheduler.cpp:2010 (HandleReschedule) Reschedule requested for id 786.
Apr 17 17:29:33 myth mythbackend[1822]: I Scheduler scheduler.cpp:2068 (HandleReschedule) Scheduled 11 items in 0.1 = 0.00 match + 0.09 place
Apr 17 17:29:38 myth mythbackend[1822]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Apr 17 17:29:40 myth mythbackend[1822]: I Scheduler scheduler.cpp:2010 (HandleReschedule) Reschedule requested for id 787.
Apr 17 17:29:40 myth mythbackend[1822]: I Scheduler scheduler.cpp:2068 (HandleReschedule) Scheduled 12 items in 0.1 = 0.00 match + 0.09 place
Apr 17 17:29:41 myth mythbackend[1822]: I Scheduler scheduler.cpp:2010 (HandleReschedule) Reschedule requested for id 788.
Apr 17 17:29:41 myth mythbackend[1822]: I Scheduler scheduler.cpp:2068 (HandleReschedule) Scheduled 13 items in 0.1 = 0.00 match + 0.14 place
Apr 17 17:29:57 myth mythbackend[1822]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Apr 17 17:29:57 myth mythbackend[1822]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: myth as a client (events: 0)
Apr 17 17:29:57 myth mythbackend[1822]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
```

---

### Post by tgm4883 on 2012-04-17
I still think it's trying to start before one of the dependencies is up. 

Try changing
```
sleep 5
```
to
```
sleep 30
```

Then check if it's running 1 minute after you've booted

---

### Post by Paulgirardin on 2012-04-17
Adding the delay was unsuccessful

---

### Post by jb5 on 2012-04-18
Had (this?) problem on a combined FE/BE system, &#8594; if wireless network not available, unable to connect to backend.

changing

IFACE!=lo

to

IFACE=lo

sorted this out for me.

Not sure why this is set up as it is, I will need to investigate further when I get the chance.

---

### Post by Paulgirardin on 2012-04-18
Thanks jb5, your suggestion worked.
I am using the original mythtv-backend.conf file with IFACE!=lo
changed to IFACE=lo.

Cheers

---

### Post by yonkiman on 2013-04-29
FYI:  Here's another reason mythbackend might not start after boot for some reason (in my case it was a partial_restore to fix some database errors).  I found that my mythbackend wasn't launching at boot (or after running mythtv-setup) because I had changed the mythtv database password to "mythtv" from the "dtageld5"-like password my system originally had.

Even though I had changed the password for the mythconverg database in:
 - the mysql mythconverg database itself,
 - /etc/apache2/sites-available/mythweb.conf
 - mythtv-setup
 - mythtv/mysql.txt

If I manually launched mythbackend everything worked fine.  But I could not get it to go back to launching at startup until I changed the password back to the one I was using before the --partial_restore...

Michael T. Dean added this comment from my thread on the mythtv mailing list:
> Yeah, the different distros try to make it easy for you by hiding the details of the MySQL password, but in so doing make it very difficult (or downright wrong?) to change the MySQL password without using the tools they provide to do so (like some kind of apt something reconfigure type black magic  or something ;).  That's why I suggested the drop/create without any GRANT (and why I put the line in the HOWTO that warns about messing with the password).

There was likely a $HOME/.mythtv/config.xml (we don't use mysql.txt anymore) that was being used in the environment of the startup script that differed from the one being used when you manually started one.


---

### Post by tgm4883 on 2013-04-29
Old thread is old. Please don't perform necromancy.

---

