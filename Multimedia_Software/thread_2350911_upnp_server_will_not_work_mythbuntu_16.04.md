---
title: "upnp server will not work mythbuntu 16.04"
date: 2017-01-28
forum: Multimedia Software
---

### Post by efolse on 2017-01-28
Ok, I guess it is offical.  I need some help.  I have installed Mythbuntu 16.4. It was a fresh install with me keeping my recordings and database from 14.04.  It is the same Gateway GT5432 that ran the 14.04 and the upnp server was working fine before the upgrade.  We could watch everything on the tv.  My problem is that I can not play anything on my Samsung LN46C630.  Everything but the media server is working fine. I have used and verified mythwelcome (to make it turn off and on to record unattended) mythfrontend with old recordings and videos, and mythbackend (except the upnp server).  I have used mythweb and use a different computer to pull it up.  Mythweb does pull up the recordings and videos.  I can play it on another computer in the tab with the flash player or download the asx file and play it on vlc.  I can play them on the frontend on the desktop.

I get "Welcome to Ubuntu 16.04.1 LTS (GNU/Linux 4.4.0-59-generic x86_64)" when I log in.  I also ran apt-cache policy mythtv-common and got:

```
efolse@efolse-GT5432:~$ apt-cache policy mythtv-common
mythtv-common:
  Installed: 2:0.28.0+fixes.20170127.9802102-0ubuntu0mythbuntu3
  Candidate: 2:0.28.0+fixes.20170127.9802102-0ubuntu0mythbuntu3
  Version table:
 *** 2:0.28.0+fixes.20170127.9802102-0ubuntu0mythbuntu3 500
        500 [http://ppa.launchpad.net/mythbuntu/0.28/ubuntu](http://ppa.launchpad.net/mythbuntu/0.28/ubuntu) xenial/main amd64 Packages
        100 /var/lib/dpkg/status
     2:0.28.0+fixes.20160413.15cf421-0ubuntu2 500
        500 [http://pubmirrors.dal.corespace.com/ubuntu](http://pubmirrors.dal.corespace.com/ubuntu) xenial/multiverse amd64 Packages
```


I copy the backend log from the most recent boot.  I do not know how to change the command line flags to make it verbose yet.  New to systemd.

```
efolse@efolse-GT5432:~$ less tem*
Jan 28 18:32:22 efolse-GT5432 mythbackend: mythbackend[1886]: C CoreContext signalhandling.cpp:305 (handleSignal) Received Terminated: Code 0, PID 1, UID 0, Value 0x00000000
Jan 28 18:35:29 efolse-GT5432 mythbackend: mythbackend[1925]: C thread_unknown mythcommandlineparser.cpp:2599 (ConfigureLogging) mythbackend version: fixes/0.28 [v0.28-114-g9802102] [www.mythtv.org](www.mythtv.org)
Jan 28 18:35:29 efolse-GT5432 mythbackend: mythbackend[1925]: C thread_unknown mythcommandlineparser.cpp:2601 (ConfigureLogging) Qt version: compile: 5.5.1, runtime: 5.5.1
Jan 28 18:35:29 efolse-GT5432 mythbackend: mythbackend[1925]: N thread_unknown mythcommandlineparser.cpp:2603 (ConfigureLogging) Enabled verbose msgs:  general
Jan 28 18:35:29 efolse-GT5432 mythbackend: mythbackend[1925]: N thread_unknown logging.cpp:920 (logStart) Setting Log Level to LOG_INFO
Jan 28 18:35:29 efolse-GT5432 mythbackend: mythbackend[1925]: I Logger logging.cpp:313 (run) Added logging to the console
Jan 28 18:35:29 efolse-GT5432 mythbackend: mythbackend[1925]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Interrupt handler
Jan 28 18:35:29 efolse-GT5432 mythbackend: mythbackend[1925]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Terminated handler
Jan 28 18:35:29 efolse-GT5432 mythbackend: mythbackend[1925]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Segmentation fault handler
Jan 28 18:35:29 efolse-GT5432 mythbackend: mythbackend[1925]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Aborted handler
Jan 28 18:35:29 efolse-GT5432 mythbackend: mythbackend[1925]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Bus error handler
Jan 28 18:35:29 efolse-GT5432 mythbackend: mythbackend[1925]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Floating point exception handler
Jan 28 18:35:29 efolse-GT5432 mythbackend: mythbackend[1925]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Illegal instruction handler
Jan 28 18:35:29 efolse-GT5432 mythbackend: mythbackend[1925]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Real-time signal 0 handler
Jan 28 18:35:29 efolse-GT5432 mythbackend: mythbackend[1925]: I thread_unknown signalhandling.cpp:194 (SetHandlerPrivate) Setup Hangup handler
Jan 28 18:35:29 efolse-GT5432 mythbackend: mythbackend[1925]: N thread_unknown mythdirs.cpp:192 (InitializeMythDirs) Using runtime prefix = /usr
Jan 28 18:35:29 efolse-GT5432 mythbackend: mythbackend[1925]: N thread_unknown mythdirs.cpp:194 (InitializeMythDirs) Using configuration directory = /home/mythtv/.mythtv
Jan 28 18:35:29 efolse-GT5432 mythbackend: mythbackend[1925]: I CoreContext mythcorecontext.cpp:266 (Init) Assumed character encoding: en_US.UTF-8
Jan 28 18:35:29 efolse-GT5432 mythbackend: mythbackend[1925]: N CoreContext mythcontext.cpp:505 (LoadDatabaseSettings) Empty LocalHostName.
Jan 28 18:35:29 efolse-GT5432 mythbackend: mythbackend[1925]: I CoreContext mythcontext.cpp:513 (LoadDatabaseSettings) Using localhost value of efolse-GT5432
Jan 28 18:35:29 efolse-GT5432 mythbackend: mythbackend[1925]: I LogForward loggingserver.cpp:295 (SyslogLogger) Added syslogging
Jan 28 18:35:29 efolse-GT5432 mythbackend: mythbackend[1925]: N CoreContext mythcorecontext.cpp:1670 (InitLocale) Setting QT default locale to en_US
Jan 28 18:35:29 efolse-GT5432 mythbackend: mythbackend[1925]: I CoreContext mythcorecontext.cpp:1703 (SaveLocaleDefaults) Current locale en_US
Jan 28 18:35:29 efolse-GT5432 mythbackend: mythbackend[1925]: N CoreContext mythlocale.cpp:123 (LoadDefaultsFromXML) Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
Jan 28 18:35:30 efolse-GT5432 mythbackend: mythbackend[1925]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jan 28 18:35:30 efolse-GT5432 mythbackend: mythbackend[1925]: I CoreContext schemawizard.cpp:120 (Compare) Current MythTV Schema Version (DBSchemaVer): 1344
Jan 28 18:35:30 efolse-GT5432 mythbackend: mythbackend[1925]: I CoreContext mythtranslation.cpp:73 (load) Loading en_us translation for module mythfrontend
Jan 28 18:35:30 efolse-GT5432 mythbackend: mythbackend[1925]: N CoreContext main_helpers.cpp:597 (run_backend) MythBackend: Starting up as the master server.
Jan 28 18:35:33 efolse-GT5432 mythbackend: mythbackend[1925]: I CoreContext recorders/dvbchannel.cpp:712 (Tune) DVBChan[1](/dev/dvb/adapter0/frontend0): Next tuning after less than 1000ms. Delaying by 1000ms
Jan 28 18:35:37 efolse-GT5432 mythbackend: mythbackend[1925]: I CoreContext recorders/dvbchannel.cpp:712 (Tune) DVBChan[5](/dev/dvb/adapter1/frontend0): Next tuning after less than 1000ms. Delaying by 1000ms
Jan 28 18:35:38 efolse-GT5432 mythbackend: mythbackend[1925]: I CoreContext programinfo.cpp:2390 (CheckProgramIDAuthorities) Found 1 distinct programid authorities
Jan 28 18:35:38 efolse-GT5432 mythbackend: mythbackend[1925]: I CoreContext housekeeper.cpp:633 (RegisterTask) Registering HouseKeeperTask 'LogClean'.
Jan 28 18:35:38 efolse-GT5432 mythbackend: mythbackend[1925]: I CoreContext housekeeper.cpp:633 (RegisterTask) Registering HouseKeeperTask 'DBCleanup'.
Jan 28 18:35:38 efolse-GT5432 mythbackend: mythbackend[1925]: I CoreContext housekeeper.cpp:633 (RegisterTask) Registering HouseKeeperTask 'ThemeUpdateNotifications'.
Jan 28 18:35:38 efolse-GT5432 mythbackend: mythbackend[1925]: I CoreContext housekeeper.cpp:633 (RegisterTask) Registering HouseKeeperTask 'RecordedArtworkUpdate'.
Jan 28 18:35:38 efolse-GT5432 mythbackend: mythbackend[1925]: I Scheduler mythdbcon.cpp:449 (getStaticCon) New static DB connectionSchedCon
Jan 28 18:35:38 efolse-GT5432 mythbackend: mythbackend[1925]: I CoreContext housekeeper.cpp:633 (RegisterTask) Registering HouseKeeperTask 'MythFillDB'.
Jan 28 18:35:38 efolse-GT5432 mythbackend: mythbackend[1925]: I CoreContext housekeeper.cpp:633 (RegisterTask) Registering HouseKeeperTask 'UpdateRadioStreams'.
Jan 28 18:35:38 efolse-GT5432 mythbackend: mythbackend[1925]: I CoreContext housekeeper.cpp:633 (RegisterTask) Registering HouseKeeperTask 'JobQueueRecover'.
Jan 28 18:35:38 efolse-GT5432 mythbackend: mythbackend[1925]: I CoreContext housekeeper.cpp:633 (RegisterTask) Registering HouseKeeperTask 'HardwareProfiler'.
Jan 28 18:35:38 efolse-GT5432 mythbackend: mythbackend[1925]: I CoreContext housekeeper.cpp:706 (Start) Starting HouseKeeper.
Jan 28 18:35:38 efolse-GT5432 mythbackend: mythbackend[1925]: I CoreContext serverpool.cpp:407 (listen) Listening on TCP 127.0.0.1:6544
Jan 28 18:35:38 efolse-GT5432 mythbackend: mythbackend[1925]: I CoreContext serverpool.cpp:407 (listen) Listening on TCP 192.168.1.65:6544
```


I know permissions are important with the upnp server.  I unmounted the two added hard drives and ran this on the mount points:
```
efolse@efolse-GT5432:/mnt$ stat 4TBone
  File: '4TBone'
  Size: 4096            Blocks: 8          IO Block: 4096   directory
Device: 807h/2055d      Inode: 2888609     Links: 2
Access: (0755/drwxr-xr-x)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2017-01-28 08:18:46.923793524 -0600
Modify: 2017-01-22 16:09:59.024537688 -0600
Change: 2017-01-22 16:09:59.024537688 -0600
 Birth: -
efolse@efolse-GT5432:/mnt$ stat Baracuda
  File: 'Baracuda'
  Size: 4096            Blocks: 8          IO Block: 4096   directory
Device: 807h/2055d      Inode: 2888619     Links: 2
Access: (0755/drwxr-xr-x)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2017-01-28 08:18:47.079791563 -0600
Modify: 2017-01-22 16:10:18.893592224 -0600
Change: 2017-01-22 16:10:18.893592224 -0600
 Birth: -
efolse@efolse-GT5432:/mnt$
```

I remounted the hard drives and did the same with the subdirectories as they are mounted.
```

efolse@efolse-GT5432:/mnt/4TBone$ stat mythtv
  File: 'mythtv'
  Size: 4096            Blocks: 8          IO Block: 4096   directory
Device: 861h/2145d      Inode: 69468161    Links: 4
Access: (0777/drwxrwxrwx)  Uid: (  123/  mythtv)   Gid: (  131/  mythtv)
Access: 2017-01-25 21:11:47.351861590 -0600
Modify: 2017-01-24 21:00:27.378741716 -0600
Change: 2017-01-25 21:02:30.476150585 -0600
 Birth: -

efolse@efolse-GT5432:/mnt/4TBone/mythtv$ stat recordings
  File: 'recordings'
  Size: 139264          Blocks: 272        IO Block: 4096   directory
Device: 861h/2145d      Inode: 69468162    Links: 2
Access: (0777/drwxrwxrwx)  Uid: (  123/  mythtv)   Gid: (  131/  mythtv)
Access: 2017-01-28 19:36:03.491492433 -0600
Modify: 2017-01-28 20:00:07.270481118 -0600
Change: 2017-01-28 20:00:07.270481118 -0600
 Birth: -
efolse@efolse-GT5432:/mnt/4TBone/mythtv$ stat livetv
  File: 'livetv'
  Size: 4096            Blocks: 8          IO Block: 4096   directory
Device: 861h/2145d      Inode: 69468163    Links: 2
Access: (0777/drwxrwxrwx)  Uid: (  123/  mythtv)   Gid: (  131/  mythtv)
Access: 2017-01-25 21:11:47.463849599 -0600
Modify: 2017-01-28 20:00:00.411178488 -0600
Change: 2017-01-28 20:00:00.411178488 -0600
 Birth: -
```
```

efolse@efolse-GT5432:/mnt/Baracuda$ ls -l mythtv
total 22804
-rw-rw-r--  1 mythtv mythtv        0 Jan 22 16:51 2041_20170122225143.ts
drwxrwxrwx 17 mythtv mythtv     4096 Jan 15  2012 archive
drwxrwxrwx  2 mythtv mythtv    57344 Jan 28 20:00 banners
drwxrwxrwx  2 mythtv mythtv    86016 Jan 28 20:00 coverart
drwxrwxrwx  2 mythtv mythtv     4096 Jan 28 20:00 DBackup
drwxrwxrwx  2 mythtv mythtv    69632 Jan 28 20:00 fanart
-rw-rw-rw-  1 mythtv mythtv       26 Aug 27  2012 lastbackuptime-efolse-desktop.log
drwxrwxrwx  2 mythtv mythtv     4096 Jan 28 20:00 live
drwxrwxrwx  3 mythtv mythtv     4096 Sep  4  2014 music
-rw-rw-rw-  1 mythtv mythtv 22960697 Aug 27  2012 mythbuntu-system-backup_efolse-desktop_20120827-0829_MBE_YESDB.tar.gz
drwxrwxrwx  5 mythtv mythtv     4096 Sep  4  2014 pictures
drwxrwxrwx  2 mythtv mythtv   135168 Jan 28 20:00 recordings
drwxrwxrwx  2 mythtv mythtv     4096 Jan 28 20:00 screenshots
drwxrwxrwx  2 mythtv mythtv     4096 Jan 28 20:00 Trailers
drwxrwxrwx  6 mythtv mythtv     4096 Jan 28 20:00 videos
efolse@efolse-GT5432:/mnt/Baracuda$
```


This is my account
```

efolse@efolse-GT5432:/mnt/Baracuda$ id efolse
uid=1000(efolse) gid=1000(efolse) groups=1000(efolse),4(adm),24(cdrom),27(sudo),30(dip),44(video),46(plugdev),114(lpadmin),118(sambashare),131(mythtv)
efolse@efolse-GT5432:/mnt/Baracuda$
```


This is mythtv
```
$ id mythtv
uid=123(mythtv) gid=131(mythtv) groups=131(mythtv),20(dialout),24(cdrom),29(audio),44(video)
```


I could not remember the command To find out who is running which server so I used top.  This is what I got:
```
Tasks: 204 total,   1 running, 203 sleeping,   0 stopped,   0 zombie
%Cpu(s): 11.1 us,  4.1 sy,  0.0 ni, 80.7 id,  3.9 wa,  0.0 hi,  0.2 si,  0.0 st
KiB Mem :  1918144 total,    83836 free,   685332 used,  1148976 buff/cache
KiB Swap:   911356 total,   910528 free,      828 used.  1006212 avail Mem

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
 1676 efolse    20   0 2779868 214440  95168 S  16.2 11.2   6:45.53 mythwelcome
 1796 mythtv    20   0 3789864 139712  62904 S  12.9  7.3   6:02.33 mythbackend
 2009 root      20   0       0      0      0 S   1.7  0.0   0:44.30 vb2-cx88[0]
 1105 mysql     20   0 1585136 204460  10064 S   0.7 10.7   0:23.89 mysqld
 5058 efolse    20   0   40520   3572   2944 R   0.7  0.2   0:00.22 top
  163 root      20   0       0      0      0 S   0.3  0.0   0:00.47 usb-storage
  587 root      20   0       0      0      0 S   0.3  0.0   0:06.58 rc0
  593 root      20   0       0      0      0 S   0.3  0.0   0:06.73 rc1
 1637 efolse    20   0  121824  19476  11592 S   0.3  1.0   2:27.78 x11vnc
 4596 root      20   0       0      0      0 S   0.3  0.0   0:00.45 kworker/0:0
    1 root      20   0  120264   6220   3776 S   0.0  0.3   0:01.93 systemd
    2 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kthreadd
    3 root      20   0       0      0      0 S   0.0  0.0   0:00.12 ksoftirqd/0
    5 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/0:+
    7 root      20   0       0      0      0 S   0.0  0.0   0:00.89 rcu_sched
    8 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcu_bh
    9 root      rt   0       0      0      0 S   0.0  0.0   0:00.02 migration/0
```


I have turned off the firewall since I have one built into the router and until I can get this straight.  The TV can see the server but does not see any videos.  I did see them when I was using mythbuntu 14.04.

Mythbuntu puts some directories for the apache server  Here is their ownerships
```
efolse@efolse-GT5432:/var/lib$ ls -l mythtv
total 52
drwxrwsr-x 2 mythtv mythtv 4096 Apr 18  2016 banners
drwxrwsr-x 2 mythtv mythtv 4096 Jul 19  2016 bare-client
drwxrwsr-x 2 mythtv mythtv 4096 Apr 18  2016 coverart
drwxrwsr-x 2 mythtv mythtv 4096 Apr 18  2016 db_backups
drwxrwsr-x 2 mythtv mythtv 4096 Apr 18  2016 fanart
drwxrwsr-x 2 mythtv mythtv 4096 Jan 23 20:32 livetv
drwxrwsr-x 2 mythtv mythtv 4096 Apr 18  2016 music
drwxrwxr-x 3 mythtv mythtv 4096 Jan 22 20:30 pictures
drwxrwsr-x 2 mythtv mythtv 4096 Jan 23 20:28 recordings
drwxrwsr-x 2 mythtv mythtv 4096 Apr 18  2016 screenshots
drwxrwsr-x 2 mythtv mythtv 4096 Apr 18  2016 streaming
drwxrwsr-x 2 mythtv mythtv 4096 Apr 18  2016 trailers
drwxrwsr-x 2 mythtv mythtv 4096 Jan 23 20:42 videos
efolse@efolse-GT5432:/var/lib$
```
under recordings
```
$ ls -l recordings
total 0
lrwxrwxrwx 1 efolse mythtv 30 Jan 23 20:28 4tb -> /mnt/4TBone/mythtv/recordings/
lrwxrwxrwx 1 efolse efolse 31 Jan 28 21:23 Baracuda -> /mnt/Baracuda/mythtv/recordings
efolse@efolse-GT5432:/var/lib/mythtv$
```


Not sure what I am missing.  Help! Thanks.

---

### Post by efolse on 2017-01-29
I have tried putting a recording in /var/lib/mythtv/recordings and deleted the links to no avail.  I then changed the ownership of the mount points "/mnt/4TBone and /mnt/Baracuda" and put the pointers back again to no avail.

---

