---
title: "Zoneminder with dedicated HDD"
date: 2014-01-29
forum: Multimedia Software
---

### Post by Eric_Longstreth on 2014-01-29
Hello Ubuntu forums,
I have installed and configured zoneminder to work with my 2 IP cameras. I can view them from a web browser. I have a second HDD for dedicated recording. I followed these directions [http://www.zoneminder.com/wiki/index.php/Using_a_dedicated_Hard_Drive](http://www.zoneminder.com/wiki/index.php/Using_a_dedicated_Hard_Drive) I then followed this part of editing my fstab to say 
[COLOR=#000000]
/dev/sdb1 /medua/Security ext4 defaults 0 2
[/COLOR]/media/Security/zoneminder/images /var/cache/zoneminder/images none defaults,bind  0 2
/media/Security/zoneminder/events /var/cache/zoneminder/events none defaults,bind 0 2

I think that my drive mounts correctly because I don't get any errors and it also is populated on the left bar on my screen. However, here in les my problem when I try to record to my second HDD I get these errors from the log and cannot figure out how to correct them.[TABLE="class: major table-sortable, width: 925"]
[TR]
[TH="class: table-th-sort table-th-sort-rev, align: left"][FONT=inherit]Date/Time[/FONT][/TH]
[TH="class: table-th-nosort, align: left"]Component[/TH]
[TH="class: table-th-nosort, align: left"]PID[/TH]
[TH="class: table-th-nosort, align: left"]Level[/TH]
[TH="class: table-th-nosort, align: left"]Message[/TH]
[TH="class: table-th-nosort, align: left"]File[/TH]
[TH="class: table-th-nosort, align: left"]Line[/TH]
[/TR]
[TR="class: table-tr-odd log-err table-tr-group-head, bgcolor: #F8F8F8"]
[TD="class: table-td-sort, bgcolor: #FFCCCC, align: left"]2014-01-29 08:47:27.133660[/TD]
[TD="bgcolor: #FFCCCC, align: left"]zmdc[/TD]
[TD="bgcolor: #FFCCCC, align: left"]1909[/TD]
[TD="bgcolor: #FFCCCC, align: left"]ERR[/TD]
[TD="bgcolor: #FFCCCC, align: left"]'zma -m 2' exited abnormally, exit status 255[/TD]
[TD="bgcolor: #FFCCCC, align: left"]zmdc.pl[/TD]
[TD="bgcolor: #FFCCCC, align: left"][/TD]
[/TR]
[TR="class: log-fat table-tr-group-head"]
[TD="class: table-td-sort, bgcolor: #FFCCCC, align: left"]2014-01-29 08:47:27.127616[/TD]
[TD="bgcolor: #FFCCCC, align: left"]zma_m2[/TD]
[TD="bgcolor: #FFCCCC, align: left"]2824[/TD]
[TD="bgcolor: #FFCCCC, align: left"]FAT[/TD]
[TD="bgcolor: #FFCCCC, align: left"]Can't change directory to 'events': No such file or directory[/TD]
[TD="bgcolor: #FFCCCC, align: left"]zm_monitor.cpp[/TD]
[TD="bgcolor: #FFCCCC, align: left"]546[/TD]
[/TR]
[TR="class: table-tr-odd log-err table-tr-group-head, bgcolor: #F8F8F8"]
[TD="class: table-td-sort, bgcolor: #FFCCCC, align: left"]2014-01-29 08:47:27.122142[/TD]
[TD="bgcolor: #FFCCCC, align: left"]zma_m2[/TD]
[TD="bgcolor: #FFCCCC, align: left"]2824[/TD]
[TD="bgcolor: #FFCCCC, align: left"]ERR[/TD]
[TD="bgcolor: #FFCCCC, align: left"]Can't make events/2: No such file or directory[/TD]
[TD="bgcolor: #FFCCCC, align: left"]zm_monitor.cpp[/TD]
[TD="bgcolor: #FFCCCC, align: left"]541[/TD]
[/TR]
[TR="class: log-err table-tr-group-head"]
[TD="class: table-td-sort, bgcolor: #FFCCCC, align: left"]2014-01-29 08:47:27.116423[/TD]
[TD="bgcolor: #FFCCCC, align: left"]zma_m2[/TD]
[TD="bgcolor: #FFCCCC, align: left"]2824[/TD]
[TD="bgcolor: #FFCCCC, align: left"]ERR[/TD]
[TD="bgcolor: #FFCCCC, align: left"]Can't make events: Permission denied[/TD]
[TD="bgcolor: #FFCCCC, align: left"]zm_monitor.cpp[/TD]
[TD="bgcolor: #FFCCCC, align: left"]529[/TD]
[/TR]
[TR="class: table-tr-odd table-tr-group-head, bgcolor: #F8F8F8"]
[TD="class: table-td-sort, align: left"]2014-01-29 08:47:27.092540[/TD]
[TD="align: left"]zmdc[/TD]
[TD="align: left"]2824[/TD]
[TD="align: left"]INF[/TD]
[TD="align: left"]'zma -m 2' started at 14/01/29 08:47:27[/TD]
[TD="align: left"]zmdc.pl[/TD]
[TD="align: left"][/TD]
[/TR]
[TR="class: table-tr-group-head"]
[TD="class: table-td-sort, align: left"]2014-01-29 08:47:27.091850[/TD]
[TD="align: left"]zmdc[/TD]
[TD="align: left"]1909[/TD]
[TD="align: left"]INF[/TD]
[TD="align: left"]'zma -m 2' starting at 14/01/29 08:47:27, pid = 2824[/TD]
[TD="align: left"]zmdc.pl[/TD]
[TD="align: left"][/TD]
[/TR]
[TR="class: table-tr-odd table-tr-group-head, bgcolor: #F8F8F8"]
[TD="class: table-td-sort, align: left"]2014-01-29 08:47:27.082730[/TD]
[TD="align: left"]zmdc[/TD]
[TD="align: left"]1909[/TD]
[TD="align: left"]INF[/TD]
[TD="align: left"]Starting pending process, zma -m 2[/TD]
[TD="align: left"]zmdc.pl[/TD]
[TD="align: left"][/TD]
[/TR]
[TR="class: table-tr-group-head"]
[TD="class: table-td-sort, align: left"]2014-01-29 08:47:02.984799[/TD]
[TD="align: left"]zmc_m2[/TD]
[TD="align: left"]1940[/TD]
[TD="align: left"]INF[/TD]
[TD="align: left"]LivingRoom: 2000 - Capturing at 6.76 fps[/TD]
[TD="align: left"]zm_monitor.cpp[/TD]
[TD="align: left"]2783[/TD]
[/TR]
[TR="class: table-tr-group-head table-tr-odd, bgcolor: #F8F8F8"]
[TD="class: table-td-sort, align: left"]2014-01-29 08:46:42.971068[/TD]
[TD="align: left"]zmc_m1[/TD]
[TD="align: left"]1933[/TD]
[TD="align: left"]INF[/TD]
[TD="align: left"]BabyRoom: 1000 - Capturing at 3.70 fps[/TD]
[TD="align: left"]zm_monitor.cpp[/TD]
[TD="align: left"]2783[/TD]
[/TR]
[TR="class: log-err table-tr-group-head"]
[TD="class: table-td-sort, bgcolor: #FFCCCC, align: left"]2014-01-29 08:44:47.139160[/TD]
[TD="bgcolor: #FFCCCC, align: left"]zmdc[/TD]
[TD="bgcolor: #FFCCCC, align: left"]1909[/TD]
[TD="bgcolor: #FFCCCC, align: left"]ERR[/TD]
[TD="bgcolor: #FFCCCC, align: left"]'zma -m 2' exited abnormally, exit status 255[/TD]
[TD="bgcolor: #FFCCCC, align: left"]zmdc.pl[/TD]
[TD="bgcolor: #FFCCCC, align: left"][/TD]
[/TR]
[TR="class: log-fat table-tr-group-head table-tr-odd, bgcolor: #F8F8F8"]
[TD="class: table-td-sort, bgcolor: #FFCCCC, align: left"]2014-01-29 08:44:47.132928[/TD]
[TD="bgcolor: #FFCCCC, align: left"]zma_m2[/TD]
[TD="bgcolor: #FFCCCC, align: left"]2781[/TD]
[TD="bgcolor: #FFCCCC, align: left"]FAT[/TD]
[TD="bgcolor: #FFCCCC, align: left"]Can't change directory to 'events': No such file or directory[/TD]
[TD="bgcolor: #FFCCCC, align: left"]zm_monitor.cpp[/TD]
[TD="bgcolor: #FFCCCC, align: left"]546[/TD]
[/TR]
[TR="class: log-err table-tr-group-head"]
[TD="class: table-td-sort, bgcolor: #FFCCCC, align: left"]2014-01-29 08:44:47.127448[/TD]
[TD="bgcolor: #FFCCCC, align: left"]zma_m2[/TD]
[TD="bgcolor: #FFCCCC, align: left"]2781[/TD]
[TD="bgcolor: #FFCCCC, align: left"]ERR[/TD]
[TD="bgcolor: #FFCCCC, align: left"]Can't make events/2: No such file or directory[/TD]
[TD="bgcolor: #FFCCCC, align: left"]zm_monitor.cpp[/TD]
[TD="bgcolor: #FFCCCC, align: left"]541[/TD]
[/TR]
[TR="class: log-err table-tr-group-head table-tr-odd, bgcolor: #F8F8F8"]
[TD="class: table-td-sort, bgcolor: #FFCCCC, align: left"]2014-01-29 08:44:47.121856[/TD]
[TD="bgcolor: #FFCCCC, align: left"]zma_m2[/TD]
[TD="bgcolor: #FFCCCC, align: left"]2781[/TD]
[TD="bgcolor: #FFCCCC, align: left"]ERR[/TD]
[TD="bgcolor: #FFCCCC, align: left"]Can't make events: Permission denied[/TD]
[TD="bgcolor: #FFCCCC, align: left"]zm_monitor.cpp[/TD]
[TD="bgcolor: #FFCCCC, align: left"]529[/TD]
[/TR]
[TR="class: table-tr-group-head"]
[TD="class: table-td-sort, align: left"]2014-01-29 08:44:47.094200[/TD]
[TD="align: left"]zmdc[/TD]
[TD="align: left"]2781[/TD]
[TD="align: left"]INF[/TD]
[TD="align: left"]'zma -m 2' started at 14/01/29 08:44:47[/TD]
[TD="align: left"]zmdc.pl[/TD]
[TD="align: left"][/TD]
[/TR]
[TR="class: table-tr-group-head table-tr-odd, bgcolor: #F8F8F8"]
[TD="class: table-td-sort, align: left"]2014-01-29 08:44:47.094190[/TD]
[TD="align: left"]zmdc[/TD]
[TD="align: left"]1909[/TD]
[TD="align: left"]INF[/TD]
[TD="align: left"]'zma -m 2' starting at 14/01/29 08:44:47, pid = 2781[/TD]
[TD="align: left"]zmdc.pl[/TD]
[TD="align: left"][/TD]
[/TR]
[TR="class: table-tr-group-head"]
[TD="class: table-td-sort, align: left"]2014-01-29 08:44:47.087320[/TD]
[TD="align: left"]zmdc[/TD]
[TD="align: left"]1909[/TD]
[TD="align: left"]INF[/TD]
[TD="align: left"]Starting pending process, zma -m 2[/TD]
[TD="align: left"]zmdc.pl[/TD]
[TD="align: left"][/TD]
[/TR]
[TR="class: table-tr-group-head table-tr-odd, bgcolor: #F8F8F8"]
[TD="class: table-td-sort, align: left"]2014-01-29 08:44:34.866772[/TD]
[TD="align: left"]zmc_m2[/TD]
[TD="align: left"]1940[/TD]
[TD="align: left"]INF[/TD]
[TD="align: left"]LivingRoom: 1000 - Capturing at 7.04 fps[/TD]
[TD="align: left"]zm_monitor.cpp[/TD]
[TD="align: left"]2783[/TD]
[/TR]
[/TABLE]
It says permission denied I have www-data being the owner on the /var/cache/zoneminder file but on the second hdd I have root being the owner. Any help would be greatly appreciated. Thank you,

---

### Post by tgalati4 on 2014-01-29
Examine the permissions of your mounts:

```
ls -la /media/Security/zoneminder
```

Verify what owner zoneminder is running:

```
ps -ef | grep zoneminder
```

The webserver uses www-data for access (including writing changes to the pages) so there is a conflict somewhere.

The other conflict to resolve is that the instructions show /usr/share/zoneminder/events (and images) as the mountpoints but you are using /var/cache/zoneminder.  So there are obviously links that point to /var/cache/zoneminder, but check the permissions of /usr/share/zoneminder/events and /usr/share/zoneminders/images.

---

### Post by Eric_Longstreth on 2014-01-29
Here is my output of the first 2 commands

eric@eric-B85H3-M:~$ ls -la /media/Security/Zonemindertotal 16
drwxr-xr-x 4 root root 4096 Jan 29 08:36 .
drwxr-xr-x 4 root root 4096 Jan 29 08:36 ..
drwxr-xr-x 2 eric eric 4096 Jan 28 23:12 events
drwxr-xr-x 2 eric eric 4096 Jan 28 23:12 images
eric@eric-B85H3-M:~$ ps -ef | grep zoneminder
eric      6530  6472  0 11:23 pts/0    00:00:00 grep --color=auto zoneminder
eric@eric-B85H3-M:~$ 

Im not sure what exactly what I need to change here. As far as /usr/share/zoneminder/events(images) I deleted those folders. I linked the media/Security/Zoneminder/events(images) to /var/cache/zoneminder/

---

