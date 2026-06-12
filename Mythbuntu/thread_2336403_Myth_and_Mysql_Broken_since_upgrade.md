---
title: "Myth and Mysql Broken since upgrade"
date: 2016-09-07
forum: Mythbuntu
---

### Post by gnoronha on 2016-09-07
```
kymoie@kymoie-Desktop:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:        16.04
Codename:       xenial

```


```
kymoie@kymoie-Desktop:~$ sudo apt-get dist-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-28 linux-headers-4.4.0-28-generic linux-image-4.4.0-28-generic linux-image-extra-4.4.0-28-generic
Use 'sudo apt autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
21 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up mysql-common (5.7.13-0ubuntu0.16.04.2) ...
update-alternatives: error: alternative path /etc/mysql/my.cnf.fallback doesn't exist
dpkg: error processing package mysql-common (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libmysqlclient20:amd64:
 libmysqlclient20:amd64 depends on mysql-common (>= 5.5); however:
  Package mysql-common is not configured yet.

dpkg: error processing package libmysqlclient20:amd64 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          dpkg: dependency problems prevent configuration of libqt5sql5-mysql:amd64:
 libqt5sql5-mysql:amd64 depends on libmysqlclient20 (>= 5.7.11); however:
  Package libmysqlclient20:amd64 is not configured yet.

dpkg: error processing package libqt5sql5-mysql:amd64 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          dpkg: dependency problems prevent configuration of libmyth-0.28-0:
 libmyth-0.28-0 depends on libqt5sql5-mysql; however:
  Package libqt5sql5-mysql:amd64 is not configured yet.

dpkg: error processing package libmyth-0.28-0 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of mythtv-common:
 mythtv-common depends on libmyth-0.28-0 (>= 2:0.28.0+fixes.20160727.e5ce273); however:
  Package libmyth-0.28-0 is not configured yet.

dpkg: error processing package mythtv-common (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of mythtv-transcode-utils:
 mythtv-transcode-utils depends on mythtv-common; however:
  Package mythtv-common is not configured yet.
 mythtv-transcode-utils depends on libmyth-0.28-0 (>= 2:0.28.0+fixes.20160727.e5ce273); however:
  Package libmyth-0.28-0 is not configured yet.

dpkg: error processing package mythtv-transcode-utils (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of mythtv-frontend:
 mythtv-frontend depends on mythtv-common; however:
  Package mythtv-common is not configured yet.
 mythtv-frontend depends on libmyth-0.28-0 (>= 2:0.28.0+fixes.20160727.e5ce273); however:
  Package libmyth-0.28-0 is not configured yet.

dpkg: error processing package mythtv-frontend (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of mytharchive:
 mytharchive depends on mythtv-transcode-utils (>= 2:0.28.0+fixes.20160727.e5ce273-0ubuntu0mythbuntu2); however:
  Package mythtv-transcode-utils is not configured yet.
 mytharchive depends on mythtv-frontend (>= 2:0.28.0+fixes.20160727.e5ce273-0ubuntu0mythbuntu2); however:
  Package mythtv-frontend is not configured yet.
 mytharchive depends on libmyth-0.28-0 (>= 2:0.28.0+fixes.20160727.e5ce273); however:
  Package libmyth-0.28-0 is not configured yet.

dpkg: error processing package mytharchive (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of mythbrowser:
 mythbrowser depends on mythtv-frontend (>= 2:0.28.0+fixes.20160727.e5ce273-0ubuntu0mythbuntu2); however:
  Package mythtv-frontend is not configured yet.
 mythbrowser depends on libmyth-0.28-0 (>= 2:0.28.0+fixes.20160727.e5ce273); however:
  Package libmyth-0.28-0 is not configured yet.

dpkg: error processing package mythbrowser (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of mythgallery:
 mythgallery depends on mythtv-frontend (>= 2:0.28.0+fixes.20160727.e5ce273-0ubuntu0mythbuntu2); however:
  Package mythtv-frontend is not configured yet.
 mythgallery depends on libmyth-0.28-0 (>= 2:0.28.0+fixes.20160727.e5ce273); however:
  Package libmyth-0.28-0 is not configured yet.

dpkg: error processing package mythgallery (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of mythgame:
 mythgame depends on mythtv-frontend (>= 2:0.28.0+fixes.20160727.e5ce273-0ubuntu0mythbuntu2); however:
  Package mythtv-frontend is not configured yet.
 mythgame depends on libmyth-0.28-0 (>= 2:0.28.0+fixes.20160727.e5ce273); however:
  Package libmyth-0.28-0 is not configured yet.

dpkg: error processing package mythgame (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of mythmusic:
 mythmusic depends on mythtv-frontend (>= 2:0.28.0+fixes.20160727.e5ce273-0ubuntu0mythbuntu2); however:
  Package mythtv-frontend is not configured yet.
 mythmusic depends on libmyth-0.28-0 (>= 2:0.28.0+fixes.20160727.e5ce273); however:
  Package libmyth-0.28-0 is not configured yet.

dpkg: error processing package mythmusic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of mythnetvision:
 mythnetvision depends on mythtv-frontend (>= 2:0.28.0+fixes.20160727.e5ce273-0ubuntu0mythbuntu2); however:
  Package mythtv-frontend is not configured yet.
 mythnetvision depends on mythbrowser (>= 2:0.28.0+fixes.20160727.e5ce273-0ubuntu0mythbuntu2); however:
  Package mythbrowser is not configured yet.
 mythnetvision depends on libmyth-0.28-0 (>= 2:0.28.0+fixes.20160727.e5ce273); however:
  Package libmyth-0.28-0 is not configured yet.

dpkg: error processing package mythnetvision (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of mythnews:
 mythnews depends on mythtv-frontend (>= 2:0.28.0+fixes.20160727.e5ce273-0ubuntu0mythbuntu2); however:
  Package mythtv-frontend is not configured yet.
 mythnews depends on libmyth-0.28-0 (>= 2:0.28.0+fixes.20160727.e5ce273); however:
  Package libmyth-0.28-0 is not configured yet.

dpkg: error processing package mythnews (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of mythweather:
 mythweather depends on mythtv-frontend (>= 2:0.28.0+fixes.20160727.e5ce273-0ubuntu0mythbuntu2); however:
  Package mythtv-frontend is not configured yet.
 mythweather depends on libmyth-0.28-0 (>= 2:0.28.0+fixes.20160727.e5ce273); however:
  Package libmyth-0.28-0 is not configured yet.

dpkg: error processing package mythweather (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of mythweb:
 mythweb depends on mythtv-common (>= 2:0.28.0+fixes.20160727.e5ce273-0ubuntu0mythbuntu2); however:
  Package mythtv-common is not configured yet.

dpkg: error processing package mythweb (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of mythplugins:
 mythplugins depends on mythgallery; however:
  Package mythgallery is not configured yet.
 mythplugins depends on mythgame; however:
  Package mythgame is not configured yet.
 mythplugins depends on mythmusic; however:
  Package mythmusic is not configured yet.
 mythplugins depends on mythnews; however:
  Package mythnews is not configured yet.
 mythplugins depends on mythweather; however:
  Package mythweather is not configured yet.
 mythplugins depends on mythweb; however:
  Package mythweb is not configured yet.
 mythplugins depends on mytharchive; however:
  Package mytharchive is not configured yet.
 mythplugins depends on mythbrowser; however:
  Package mythbrowser is not configured yet.
 mythplugins depends on mythnetvision; however:
  Package mythnetvision is not configured yet.

dpkg: error processing package mythplugins (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of mythtv-backend:
 mythtv-backend depends on mythtv-common; however:
  Package mythtv-common is not configured yet.
 mythtv-backend depends on mythtv-transcode-utils; however:
  Package mythtv-transcode-utils is not configured yet.
 mythtv-backend depends on libmyth-0.28-0 (>= 2:0.28.0+fixes.20160727.e5ce273); however:
  Package libmyth-0.28-0 is not configured yet.

dpkg: error processing package mythtv-backend (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of mythtv-database:
 mythtv-database depends on mythtv-common; however:
  Package mythtv-common is not configured yet.

dpkg: error processing package mythtv-database (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of mythtv-backend-master:
 mythtv-backend-master depends on mythtv-database; however:
  Package mythtv-database is not configured yet.
 mythtv-backend-master depends on mythtv-backend; however:
  Package mythtv-backend is not configured yet.

dpkg: error processing package mythtv-backend-master (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythtv-dbg:
 mythtv-dbg depends on mythtv-backend (= 2:0.28.0+fixes.20160727.e5ce273-0ubuntu0mythbuntu2) | mythtv-frontend (= 2:0.28.0+fixes.20160727.e5ce273-0ubuntu0mythbuntu2); however:
  Package mythtv-backend is not configured yet.
  Package mythtv-frontend is not configured yet.

No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            dpkg: error processing package mythtv-dbg (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-common
 libmysqlclient20:amd64
 libqt5sql5-mysql:amd64
 libmyth-0.28-0
 mythtv-common
 mythtv-transcode-utils
 mythtv-frontend
 mytharchive
 mythbrowser
 mythgallery
 mythgame
 mythmusic
 mythnetvision
 mythnews
 mythweather
 mythweb
 mythplugins
 mythtv-backend
 mythtv-database
 mythtv-backend-master
 mythtv-dbg
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Any ideas where to start ?

---

### Post by ajgreeny on 2016-09-08
Please use **Code-Tags** for terminal output in future posts.  It makes the output much easier to read by formatting the output as seen in terminal.

See my signature below for a **How-to**

---

### Post by uteck on 2016-09-11
You can see the error on the first package:
update-alternatives: error: alternative path /etc/mysql/my.cnf.fallback doesn't exist

you can make that file with a copy of /etc/mysql/my.cnf named my.cnf.fallback then mysql-common should install.

---

### Post by gnoronha on 2016-09-13
Thanks that solved my install issue 

now it doesn't appear to be connecting to the mysql getting the same setup screens again and again 

attempting an upgrade to mythtv 0.28 see if that fixes something magically

---

### Post by gnoronha on 2016-09-13
got mythtv-backend working but somehow lost my database in the upgrade
```

kymoie@kymoie-Desktop:/var/lib$ ls -la mysql*
mysql:
total 110644
drwxr-xr-x  5 mysql mysql     4096 Sep 13 19:19 .
drwxr-xr-x 95 root  root      4096 Sep 13 19:19 ..
-rw-rw----  1 mysql mysql    16384 Sep 13 19:19 aria_log.00000001
-rw-rw----  1 mysql mysql       52 Sep 13 19:19 aria_log_control
-rw-r--r--  1 root  root         0 Sep 13 19:19 debian-10.0.flag
-rw-rw----  1 mysql mysql 12582912 Sep 13 19:19 ibdata1
-rw-rw----  1 mysql mysql 50331648 Sep 13 19:19 ib_logfile0
-rw-rw----  1 mysql mysql 50331648 Jul  3 21:49 ib_logfile1
-rw-rw----  1 mysql mysql        0 Jul  3 21:50 multi-master.info
drwx------  2 mysql mysql     4096 Sep 13 19:19 mysql
-rw-------  1 mysql mysql       15 Jul  3 21:50 mysql_upgrade_info
drwx------  2 mysql mysql    12288 Sep 13 19:10 mythconverg
drwx------  2 mysql mysql     4096 Sep 13 19:19 performance_schema

mysql-5.7:
total 116792
drwxr-xr-x  7 mysql mysql     4096 Jul  3 21:49 .
drwxr-xr-x 95 root  root      4096 Sep 13 19:19 ..
-rw-rw----  1 mysql mysql       56 May  3  2015 auto.cnf
-rw-r--r--  1 mysql mysql        0 May  3  2015 debian-5.5.flag
-rw-r--r--  1 mysql mysql        0 Apr 24 08:42 debian-5.6.flag
-rw-r--r--  1 mysql mysql        0 May  7 22:24 debian-5.7.flag
-rw-r-----  1 mysql mysql      679 May  7 22:27 ib_buffer_pool
-rw-rw----  1 mysql mysql 18874368 May  7 22:27 ibdata1
-rw-r-----  1 mysql mysql 50331648 May  7 22:27 ib_logfile0
-rw-r-----  1 mysql mysql 50331648 May  7 17:36 ib_logfile1
drwx------  4 mysql mysql     4096 May 11 21:13 mysql
drwx------  2 mysql mysql     4096 May  7 15:54 mysql_backup1
-rw-rw----  1 mysql mysql        6 May  3  2015 mysql_upgrade_info
drwx------  2 mysql mysql    20480 May  7 16:06 mythconverg
drwx------  2 mysql mysql     4096 Apr 24 08:42 performance_schema
drwx------  2 mysql mysql     4096 Sep  4  2012 test

```

can I just move the mythconverg file from mysql-5.7 to mysql and it will work ? or do I have to downgrade to 5.7 not sure how tried using apt-get and it complained.

---

### Post by uteck on 2016-09-17
Have you tried that yet?  I think that will work, and would not hurt the copy it over and try.  Just make the permissions stay the same.

---

### Post by bruban2 on 2016-09-18
I'm also having many problems with my upgrade, though my database appears to be OK now.

Under my Ubuntu 16.04.1, the upgrade process has held back mysql v5.7.

```

root@mythtv:/# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  mysql-server-5.7 mysql-server-core-5.7
0 to upgrade, 0 to newly install, 0 to remove and 2 not to upgrade.

```

I suggest ensuring that you keep to this version. I've seen many reports of considerable problems with later versions of mysql, due to changes that Oracle are starting to make to the application. A number of people have started to move to Mariadb, but this is not something to be undertaken lightly. Keep with mysql 5.7 for now.


Regarding your database backup, check the location that you had configured mythtv (via mythfrontend) to place your database backups. You may find a backup there that was created during the upgrade process. In my case that was /var/mythtv/db_backups with the filename starting with the name mythconverg*.

If you're not sure where it is, try searching for it with find under a terminal, e.g.:

```

  sudo find / -name mythconverg* -print;

```

I hope this helps.

---

