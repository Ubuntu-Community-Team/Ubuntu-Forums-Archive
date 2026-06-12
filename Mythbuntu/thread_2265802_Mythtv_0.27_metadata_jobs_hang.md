---
title: "Mythtv 0.27 metadata jobs hang"
date: 2015-02-17
forum: Mythbuntu
---

### Post by JimLS on 2015-02-17
Running 0.27.4+fixes under 14.04.  I thought metadata was working and it quit but I could be wrong.  I know it doesn't work now.  I am recording OTA ATSC and have schedules direct.  All (or at least most) metadata jobs cause the job queue to get stuck and all future metadata and commercial flagging jobs don't happen.  I can go in with myphpadmin and kill the job and the commercial flagging happens until it hits another metadata job.  If I just turn off metadata what will I be loosing?  I did some checking and did a tail of the backend log:

```

myth@myth-14:~$ tail /var/log/mythtv/mythbackend.log
Feb 17 18:29:02 myth-14 mythbackend: mythbackend[1522]: I MetadataDownload metadatagrabber.cpp:455 (RunGrabber) Running Grabber: /usr/share/mythtv/metadata/Television/ttvdb.py -l en -a US -C 270261
Feb 17 18:29:07 myth-14 mythbackend: mythbackend[1522]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Monitor
Feb 17 18:29:07 myth-14 mythbackend: mythbackend[1522]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: myth-14 as a client (events: 0)
Feb 17 18:29:09 myth-14 mythbackend: mythbackend[1522]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Monitor
Feb 17 18:29:09 myth-14 mythbackend: mythbackend[1522]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: myth-14 as a client (events: 0)
Feb 17 18:29:13 myth-14 mythbackend: mythbackend[1522]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Monitor
Feb 17 18:29:13 myth-14 mythbackend: mythbackend[1522]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: myth-14 as a client (events: 0)
Feb 17 18:29:21 myth-14 mythbackend: mythbackend[1522]: I ProcessRequest mainserver.cpp:1446 (HandleAnnounce) MainServer::ANN Monitor
Feb 17 18:29:21 myth-14 mythbackend: mythbackend[1522]: I ProcessRequest mainserver.cpp:1448 (HandleAnnounce) adding: myth-14 as a client (events: 0)
Feb 17 18:34:57 myth-14 mythbackend: mythbackend[1522]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
myth@myth-14:~$


```

I did a "ps aux" as root and got some things that look to be related (not the whole output):

```

www-data 12898  0.0  1.0 332856 21308 ?        S    Feb15   0:00 /usr/sbin/apache2 -k start
mythtv   13997  0.0  0.0   4444   108 ?        S    Feb16   0:00 sh -c /usr/bin/mythmetadatalookup -j 149 --ve
mythtv   13998  0.2  1.1 1191848 23044 ?       SNl  Feb16   7:48 /usr/bin/mythmetadatalookup -j 149 --verbose
mythtv   14039  0.0  0.6 101008 12452 ?        SN   Feb16   0:00 python /usr/share/mythtv/metadata/Television/
mythtv   15777  0.0  0.0   4444   108 ?        S    01:38   0:00 sh -c /usr/bin/mythmetadatalookup -j 155 --ve
mythtv   15778  0.2  1.1 1191848 23148 ?       SNl  01:38   3:31 /usr/bin/mythmetadatalookup -j 155 --verbose
mythtv   15819  0.0  0.6 100500 12340 ?        SN   01:38   0:00 python /usr/share/mythtv/metadata/Television/
root     16390  0.0  0.1  76856  2108 ?        Ss   07:35   0:00 /usr/sbin/cupsd -f
myth     16613  0.0  0.0   4444   340 ?        S    10:38   0:00 /bin/sh /usr/bin/mythfrontend --service
myth     16622  9.1 12.4 5240488 255236 ?      Sl   10:38  58:45 /usr/bin/mythfrontend.real --syslog local7
www-data 16977  0.0  0.8 329980 17804 ?        S    16:52   0:00 /usr/sbin/apache2 -k start
mythtv   16988  0.0  0.5 100244 11996 ?        S    16:53   0:00 python /usr/share/mythtv/metadata/Television/
mythtv   17024  0.0  0.6 100908 12592 ?        S    16:53   0:00 python /usr/share/mythtv/metadata/Television/
mythtv   17033  0.0  0.6 101088 12572 ?        S    16:53   0:00 python /usr/share/mythtv/metadata/Television/
mythtv   17127  0.0  0.0   4444   112 ?        S    17:50   0:00 sh -c /usr/bin/mythmetadatalookup -j 157 --ve
mythtv   17128  0.3  1.1 1191860 23940 ?       SNl  17:50   0:42 /usr/bin/mythmetadatalookup -j 157 --verbose
mythtv   17169  0.0  0.5 100244 12180 ?        SN   17:50   0:00 python /usr/share/mythtv/metadata/Television/
root     17175  0.0  0.0 111848  1856 ?        Ss   18:00   0:00 sshd: myth [priv]
myth     17234  0.0  0.0 111848  1704 ?        D    18:00   0:00 sshd: myth@pts/3
myth     17235  0.0  0.1  26972  3136 pts/3    Ss   18:00   0:00 -bash
mythtv   17344  0.0  0.6 101496 13380 ?        S    18:28   0:00 python /usr/share/mythtv/metadata/Television/
mythtv   17361  0.0  0.6 101524 13444 ?        S    18:29   0:00 python /usr/share/mythtv/metadata/Television/
root     17439  0.0  0.0      0     0 ?        S    19:31   0:00 [kworker/1:2]


```

What should I check?

---

