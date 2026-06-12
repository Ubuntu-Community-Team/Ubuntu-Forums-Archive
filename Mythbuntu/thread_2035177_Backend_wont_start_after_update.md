---
title: "Backend wont start after update"
date: 2012-07-30
forum: Mythbuntu
---

### Post by Sctmon on 2012-07-30
I don't update my mythtv system all that often because something usually breaks! I had 414 updates pending so went for it and now the backend will not start.
There was a crash report which popped up after the system restarted which mentioned something about 0.25.fixes..... failed to install... but didn't get a chance to note the message down properly.

The frontend will not connect to the backend and sudo /etc/init.d/mythtv-backend start returns start: job failed to start.

Can anyone offer any suggestions as where to start with this? I assume that whatever the failed update 0.25.fixes...etc is the problem!

Ubuntu 12.04,  0.25 update repositories

---

### Post by Lester_Burnham on 2012-07-30
Hi,

Are there any broken packages in synaptic?
Did you copy the errors from the install terminal. A lot of the time, you will find your answers in here. Try running updates again and re-check.
Check out /var/log/dpkg.log

Lesrer

---

### Post by Sctmon on 2012-07-30
I did try running update again a few time but the system was up to date and no mention of broken packages. I will have a look at the logs when I get home tonight, I wasnt sure which log to start with.

---

### Post by Sctmon on 2012-07-30
Ok, I got this when checking for broken packages

scott@MythtvMain:~$ sudo apt-get install -f
[sudo] password for scott: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  gnome-games-data
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up mythtv-backend (2:0.25.2+fixes.20120730.a72e341-0ubuntu0mythbuntu4) ...
start: Job failed to start
invoke-rc.d: initscript mythtv-backend, action "start" failed.
dpkg: error processing mythtv-backend (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mythtv:
 mythtv depends on mythtv-backend; however:
  Package mythtv-backend is not configured yet.
dpkg: error processing mythtv (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-backend-master:
 mythtv-backend-master depends on mythtv-backend; however:
  Package mythtv-backend is not configured yet.
dpkg: error processing mythtv-backend-master (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                                       Errors were encountered while processing:
 mythtv-backend
 mythtv
 mythtv-backend-master
E: Sub-process /usr/bin/dpkg returned an error code (1)

I don't really want to have a go and break things further so any advice on where to go from here?

---

### Post by tgm4883 on 2012-07-30
> **Sctmon said:**
> Ok, I got this when checking for broken packages

scott@MythtvMain:~$ sudo apt-get install -f
[sudo] password for scott: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  gnome-games-data
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up mythtv-backend (2:0.25.2+fixes.20120730.a72e341-0ubuntu0mythbuntu4) ...
start: Job failed to start
invoke-rc.d: initscript mythtv-backend, action "start" failed.
dpkg: error processing mythtv-backend (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mythtv:
 mythtv depends on mythtv-backend; however:
  Package mythtv-backend is not configured yet.
dpkg: error processing mythtv (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-backend-master:
 mythtv-backend-master depends on mythtv-backend; however:
  Package mythtv-backend is not configured yet.
dpkg: error processing mythtv-backend-master (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                                       Errors were encountered while processing:
 mythtv-backend
 mythtv
 mythtv-backend-master
E: Sub-process /usr/bin/dpkg returned an error code (1)

I don't really want to have a go and break things further so any advice on where to go from here?

Please post your /etc/init/mythtv-backend.conf file

---

### Post by Sctmon on 2012-07-30
Here it is!

# MythTV Backend service

description     "MythTV Backend"
author          "Mario Limonciello <superm1@ubuntu.com>"

start on (local-filesystems and net-device-up IFACE!=lo and started udev-finish)
stop on runlevel [016]

#expect fork
respawn
respawn limit 2 3600

pre-start script 
    dvb-fe-tool --adapter=1 --frontend=0 --set-delsys=DVBT
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

---

### Post by tgm4883 on 2012-07-30
> **Sctmon said:**
> Here it is!

# MythTV Backend service

description     "MythTV Backend"
author          "Mario Limonciello <superm1@ubuntu.com>"

start on (local-filesystems and net-device-up IFACE!=lo and started udev-finish)
stop on runlevel [016]

#expect fork
respawn
respawn limit 2 3600

pre-start script 
    dvb-fe-tool --adapter=1 --frontend=0 --set-delsys=DVBT
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

Couple things

1) Please use code brackets when posting code snippets so it preserves whitespace (see below for examples)

2) Is mysql running?
```
sudo service mysql status
```

3) Are you able to start the backend manually 
```
/usr/bin/mythbackend --syslog local7 --user mythtv
```

---

### Post by Sctmon on 2012-07-30
mysql does seem to be running :

```
mysql start/running, process 1141
```and this is the output from trying to start the backend

```
2012-07-30 22:49:49.972386 C  mythbackend version: fixes/0.25 [v0.25.2-9-ga72e341] www.mythtv.org
2012-07-30 22:49:49.972403 C  Qt version: compile: 4.8.1, runtime: 4.8.1
2012-07-30 22:49:49.972405 N  Enabled verbose msgs:  general
2012-07-30 22:49:49.972420 N  Setting Log Level to LOG_INFO
2012-07-30 22:49:49.972452 I  Added logging to the console
2012-07-30 22:49:49.972465 I  Added syslogging to facility local7
2012-07-30 22:49:49.972469 I  Added database logging to table logging
2012-07-30 22:49:49.972533 N  Setting up SIGHUP handler
2012-07-30 22:49:49.972578 N  Using runtime prefix = /usr
2012-07-30 22:49:49.972610 N  Using configuration directory = /home/mythtv/.mythtv
2012-07-30 22:49:49.972689 I  Assumed character encoding: en_GB.UTF-8
2012-07-30 22:49:49.973284 N  Empty LocalHostName.
2012-07-30 22:49:49.973313 I  Using localhost value of MythtvMain
2012-07-30 22:49:49.998706 N  Setting QT default locale to en_GB
2012-07-30 22:49:49.998844 I  Current locale en_GB
2012-07-30 22:49:49.998931 N  Reading locale defaults from /usr/share/mythtv//locales/en_gb.xml
2012-07-30 22:49:50.011175 I  Current MythTV Schema Version (DBSchemaVer): 1299
2012-07-30 22:49:50.011778 I  Loading en_gb translation for module mythfrontend
2012-07-30 22:49:50.012941 N  MythBackend: Starting up as the master server.
2012-07-30 22:49:50.019758 W  DVBChan(1:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
            eno: No such file or directory (2)
2012-07-30 22:49:50.019781 E  DVBChan(1:/dev/dvb/adapter0/frontend0): Failed to open DVB frontend device due to fatal error or too many attempts.
2012-07-30 22:49:50.019796 E  ChannelBase: CreateChannel() Error: Failed to open device /dev/dvb/adapter0/frontend0
2012-07-30 22:49:50.019867 E  Problem with capture cardsCard 1failed init
2012-07-30 22:49:50.021821 W  DVBChan(2:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
            eno: No such file or directory (2)
2012-07-30 22:49:50.021843 E  DVBChan(2:/dev/dvb/adapter0/frontend0): Failed to open DVB frontend device due to fatal error or too many attempts.
2012-07-30 22:49:50.021857 E  ChannelBase: CreateChannel() Error: Failed to open device /dev/dvb/adapter0/frontend0
2012-07-30 22:49:50.021890 E  Problem with capture cardsCard 2failed init
2012-07-30 22:49:50.023485 W  DVBChan(3:/dev/dvb/adapter1/frontend0): Opening DVB frontend device failed.
            eno: No such file or directory (2)
2012-07-30 22:49:50.023505 E  DVBChan(3:/dev/dvb/adapter1/frontend0): Failed to open DVB frontend device due to fatal error or too many attempts.
2012-07-30 22:49:50.023518 E  ChannelBase: CreateChannel() Error: Failed to open device /dev/dvb/adapter1/frontend0
2012-07-30 22:49:50.023544 E  Problem with capture cardsCard 3failed init
2012-07-30 22:49:50.025193 W  DVBChan(4:/dev/dvb/adapter1/frontend0): Opening DVB frontend device failed.
            eno: No such file or directory (2)
2012-07-30 22:49:50.025211 E  DVBChan(4:/dev/dvb/adapter1/frontend0): Failed to open DVB frontend device due to fatal error or too many attempts.
2012-07-30 22:49:50.025224 E  ChannelBase: CreateChannel() Error: Failed to open device /dev/dvb/adapter1/frontend0
2012-07-30 22:49:50.025252 E  Problem with capture cardsCard 4failed init
2012-07-30 22:49:50.025275 W  MythBackend: No valid capture cards are defined in the database.
2012-07-30 22:49:50.028020 I  Found 7 distinct programid authorities
2012-07-30 22:49:50.028511 I  New static DB connectionSchedCon
2012-07-30 22:49:50.037288 E  Failed listening on TCP 127.0.0.1:6544 - Error 8: The bound address is already in use
2012-07-30 22:49:50.037356 E  MediaServer::HttpServer Create Error
2012-07-30 22:49:50.039295 E  Failed listening on TCP 127.0.0.1:6543 - Error 8: The bound address is already in use
2012-07-30 22:49:50.039326 C  Backend exiting, MainServer initialization error.
2012-07-30 22:50:00.033410 I  Running housekeeping thread

```I also just noticed that after updating the system the dev/dvb folder is now gone. I will have a go at building the drivers again to see if it helps.

---

### Post by tgm4883 on 2012-07-30
> **Sctmon said:**
> mysql does seem to be running :

```
mysql start/running, process 1141
```and this is the output from trying to start the backend

```
2012-07-30 22:49:49.972386 C  mythbackend version: fixes/0.25 [v0.25.2-9-ga72e341] www.mythtv.org
2012-07-30 22:49:49.972403 C  Qt version: compile: 4.8.1, runtime: 4.8.1
2012-07-30 22:49:49.972405 N  Enabled verbose msgs:  general
2012-07-30 22:49:49.972420 N  Setting Log Level to LOG_INFO
2012-07-30 22:49:49.972452 I  Added logging to the console
2012-07-30 22:49:49.972465 I  Added syslogging to facility local7
2012-07-30 22:49:49.972469 I  Added database logging to table logging
2012-07-30 22:49:49.972533 N  Setting up SIGHUP handler
2012-07-30 22:49:49.972578 N  Using runtime prefix = /usr
2012-07-30 22:49:49.972610 N  Using configuration directory = /home/mythtv/.mythtv
2012-07-30 22:49:49.972689 I  Assumed character encoding: en_GB.UTF-8
2012-07-30 22:49:49.973284 N  Empty LocalHostName.
2012-07-30 22:49:49.973313 I  Using localhost value of MythtvMain
2012-07-30 22:49:49.998706 N  Setting QT default locale to en_GB
2012-07-30 22:49:49.998844 I  Current locale en_GB
2012-07-30 22:49:49.998931 N  Reading locale defaults from /usr/share/mythtv//locales/en_gb.xml
2012-07-30 22:49:50.011175 I  Current MythTV Schema Version (DBSchemaVer): 1299
2012-07-30 22:49:50.011778 I  Loading en_gb translation for module mythfrontend
2012-07-30 22:49:50.012941 N  MythBackend: Starting up as the master server.
2012-07-30 22:49:50.019758 W  DVBChan(1:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
            eno: No such file or directory (2)
2012-07-30 22:49:50.019781 E  DVBChan(1:/dev/dvb/adapter0/frontend0): Failed to open DVB frontend device due to fatal error or too many attempts.
2012-07-30 22:49:50.019796 E  ChannelBase: CreateChannel() Error: Failed to open device /dev/dvb/adapter0/frontend0
2012-07-30 22:49:50.019867 E  Problem with capture cardsCard 1failed init
2012-07-30 22:49:50.021821 W  DVBChan(2:/dev/dvb/adapter0/frontend0): Opening DVB frontend device failed.
            eno: No such file or directory (2)
2012-07-30 22:49:50.021843 E  DVBChan(2:/dev/dvb/adapter0/frontend0): Failed to open DVB frontend device due to fatal error or too many attempts.
2012-07-30 22:49:50.021857 E  ChannelBase: CreateChannel() Error: Failed to open device /dev/dvb/adapter0/frontend0
2012-07-30 22:49:50.021890 E  Problem with capture cardsCard 2failed init
2012-07-30 22:49:50.023485 W  DVBChan(3:/dev/dvb/adapter1/frontend0): Opening DVB frontend device failed.
            eno: No such file or directory (2)
2012-07-30 22:49:50.023505 E  DVBChan(3:/dev/dvb/adapter1/frontend0): Failed to open DVB frontend device due to fatal error or too many attempts.
2012-07-30 22:49:50.023518 E  ChannelBase: CreateChannel() Error: Failed to open device /dev/dvb/adapter1/frontend0
2012-07-30 22:49:50.023544 E  Problem with capture cardsCard 3failed init
2012-07-30 22:49:50.025193 W  DVBChan(4:/dev/dvb/adapter1/frontend0): Opening DVB frontend device failed.
            eno: No such file or directory (2)
2012-07-30 22:49:50.025211 E  DVBChan(4:/dev/dvb/adapter1/frontend0): Failed to open DVB frontend device due to fatal error or too many attempts.
2012-07-30 22:49:50.025224 E  ChannelBase: CreateChannel() Error: Failed to open device /dev/dvb/adapter1/frontend0
2012-07-30 22:49:50.025252 E  Problem with capture cardsCard 4failed init
2012-07-30 22:49:50.025275 W  MythBackend: No valid capture cards are defined in the database.
2012-07-30 22:49:50.028020 I  Found 7 distinct programid authorities
2012-07-30 22:49:50.028511 I  New static DB connectionSchedCon
2012-07-30 22:49:50.037288 E  Failed listening on TCP 127.0.0.1:6544 - Error 8: The bound address is already in use
2012-07-30 22:49:50.037356 E  MediaServer::HttpServer Create Error
2012-07-30 22:49:50.039295 E  Failed listening on TCP 127.0.0.1:6543 - Error 8: The bound address is already in use
2012-07-30 22:49:50.039326 C  Backend exiting, MainServer initialization error.
2012-07-30 22:50:00.033410 I  Running housekeeping thread

```I also just noticed that after updating the system the dev/dvb folder is now gone. I will have a go at building the drivers again to see if it helps.

Progress. What is the output of

```
sudo service mythtv-backend status
```

and also

```
ps aux | grep backend
```

---

### Post by Sctmon on 2012-07-31
Hi,
The output is as follows
> 
scott@MythtvMain:~$ sudo service mythtv-backend status
[sudo] password for scott: 
mythtv-backend stop/waiting
scott@MythtvMain:~$ ps aux | grep backend
scott     2866  0.0  0.0   8100   888 pts/1    S+   06:35   0:00 grep --color=auto backend
Just starting to build the V4L-DVB Device drivers again now

---

### Post by tgm4883 on 2012-07-31
> **Sctmon said:**
> Hi,
The output is as follows
Just starting to build the V4L-DVB Device drivers again now

Weird. If there isn't a backend process running, what is using those ports?

---

### Post by Sctmon on 2012-07-31
Not sure but building the V4L-DVB drivers again did not work and they still won't load either.

A bunch of new updates appeared again this morning and they all installed except the 3 mythtv ones which failed again with the same error.

In the mean time I have re installed 12.04 on another drive, updated it, built the drivers and it works. I would like figure out what happened but it seems like it will be quicker continue on with the new install and copy the database over. I did build this system with this in mind with all the drives in an external array.

I could use any tips on a complete system backup solution though. I use to use a script i wrote that makes a copy of the entire file system and database in an archive before installing updates but something a bit neater would good.

---

