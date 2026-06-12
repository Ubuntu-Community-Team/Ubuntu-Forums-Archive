---
title: "rediculous memory usage"
date: 2010-04-28
forum: Mythbuntu
---

### Post by lennardw on 2010-04-28
Hi,

I'm a new Mythbuntu user, using Mythbuntu 9.10 patched to the latest current version. My box has 2GB of RAM, of which 512MB is allocated for the videocard.

I noticed that my box was swapping some times so I checked out the memory load. I noticed that mythfrontend and mythwelcome are using rediculous amounts of memory (approx 230 and 270MB):

```
lennard@wynne:~$ uptime
 20:06:20 up  6:58,  2 users,  load average: 0.00, 0.00, 0.00
lennard@wynne:~$ ps aux --sort size | tail -10
www-data 21006  0.0  0.6 207108  9820 ?        S    17:46   0:00 /usr/sbin/apache2 -k start
www-data  2399  0.0  0.6 207192  9432 ?        S    13:08   0:00 /usr/sbin/apache2 -k start
www-data 21001  0.0  0.7 208020 10916 ?        S    17:46   0:01 /usr/sbin/apache2 -k start
www-data 21008  0.0  0.7 208324 10892 ?        S    17:46   0:00 /usr/sbin/apache2 -k start
www-data 21005  0.0  0.8 209564 12364 ?        S    17:46   0:01 /usr/sbin/apache2 -k start
syslog     960  0.0  0.1 125916  1560 ?        Sl   13:08   0:00 rsyslogd -c4
mysql     1578  0.2  2.3 278988 36760 ?        Sl   13:08   0:54 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --socket=/var/run/mysqld/mysqld.sock --port=3306
mythtv    2565  0.1  3.9 598644 60776 ?        Sl   13:08   0:37 /usr/bin/mythbackend --logfile /var/log/mythtv/mythbackend.log
lennard   1234  6.3 15.0 723516 232216 ?       Sl   20:04   0:05 /usr/bin/mythfrontend.real
lennard  31954  0.6 17.6 698004 271712 ?       Sl   15:11   1:46 mythwelcome

```

(the backend is using about 60MB)


Is this normal for Myth? (it's not doing anything at the moment) or is there some config of mine that causes this behaviour?

---

### Post by LowSky on 2010-04-28
Well you really dont need 512MB allocated to a video card in Linux, turn that down to 64 or 128 that should be more than plenty.

Otherwise I wouldn't be too worried on he size. Think of it this way Firefox normall used about 50MB after opening a few forum pages. And with the way Linux caches data, those numbers are really not that bad.

---

### Post by lennardw on 2010-04-28
Are you sure about that?

According to the MythTV [system requirements]("http://www.mythtv.org/docs/mythtv-HOWTO-3.html") 512MB should be sufficient for a Front and backend role. If this behavior is 'normal' than the rest of the OS has little more than 10MB left :-)

230MB for a glorified daemon that turns my box off and on, and 270MB for a few pictures in a menu-form is a bit much if you ask me.

As for the videomemory. I read somewhere that 512MB is advised for HD-related stuff. I was planning on putting an extra 2GB in anyway, so it's not that much of a problem, I just find it rediculously high memory usage.


N.B. I don't use Firefox for that specific reason.

---

### Post by tgm4883 on 2010-04-28
How do you know your machine is swapping?

---

### Post by lennardw on 2010-04-28
I was monitoring it's activity, and noticed high CPU wait-times. Then I check my io, and noticed there was lots of disk paging.

My box isn't swapping when doing nothing, but it is swapping while transcoding and if it's doing a few other things too. The fact that is swaps sometimes made me look at the processes.

---

### Post by LowSky on 2010-04-28
can you post the output of these commands

```
top
```

```
free
```

---

### Post by lennardw on 2010-04-28
As requested:
```

lennard@wynne:~$ top
top - 21:42:53 up 52 min,  2 users,  load average: 0.08, 0.02, 0.01
Tasks: 185 total,   1 running, 180 sleeping,   0 stopped,   4 zombie
Cpu(s):  1.6%us,  1.0%sy,  0.0%ni, 97.1%id,  0.3%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1539372k total,   824368k used,   715004k free,    22960k buffers
Swap:  4000144k total,        0k used,  4000144k free,   244116k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 2414 lennard   20   0  768m 289m  42m S   13 19.3   5:02.81 mythfrontend.re
 2613 lennard   20   0 19260 1296  884 R    4  0.1   0:00.06 top
    1 root      20   0 19452 1756 1176 S    0  0.1   0:01.51 init
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0
    4 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1
    7 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1
    9 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/2
   10 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/2
   11 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/2
   12 root      RT  -5     0    0    0 S    0  0.0   0:00.01 migration/3
   13 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/3
   14 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/3
   15 root      15  -5     0    0    0 S    0  0.0   0:00.01 events/0
   16 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/1
   17 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/2
   18 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/3
   19 root      15  -5     0    0    0 S    0  0.0   0:00.00 cpuset
   20 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper
   21 root      15  -5     0    0    0 S    0  0.0   0:00.00 netns
   22 root      15  -5     0    0    0 S    0  0.0   0:00.00 async/mgr
   23 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/0
   24 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/1
   25 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/2
   26 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/3
   27 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/0
   28 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1
   29 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/2
   30 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/3
   31 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid
   32 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify
   33 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpi_hotplug
   34 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata/0
   35 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata/1
   36 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata/2
   37 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata/3
   38 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata_aux
   39 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd
   40 root      15  -5     0    0    0 S    0  0.0   0:00.00 khubd
   41 root      15  -5     0    0    0 S    0  0.0   0:00.00 kseriod
   42 root      15  -5     0    0    0 S    0  0.0   0:00.00 kmmcd
   43 root      15  -5     0    0    0 S    0  0.0   0:00.00 bluetooth
   44 root      20   0     0    0    0 S    0  0.0   0:00.00 khungtaskd
   45 root      20   0     0    0    0 S    0  0.0   0:00.00 pdflush
   46 root      20   0     0    0    0 S    0  0.0   0:00.00 pdflush
   47 root      15  -5     0    0    0 S    0  0.0   0:00.00 kswapd0
   48 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/0
   49 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/1
   50 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/2
   51 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/3
   52 root      15  -5     0    0    0 S    0  0.0   0:00.00 ecryptfs-kthrea
   53 root      15  -5     0    0    0 S    0  0.0   0:00.00 crypto/0
   54 root      15  -5     0    0    0 S    0  0.0   0:00.00 crypto/1
   55 root      15  -5     0    0    0 S    0  0.0   0:00.00 crypto/2
   56 root      15  -5     0    0    0 S    0  0.0   0:00.00 crypto/3
   62 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_0
   63 root      15  -5     0    0    0 S    0  0.0   0:00.52 scsi_eh_1
   64 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_2
   65 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_3
   66 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_4

```

and
```

lennard@wynne:~$ free
             total       used       free     shared    buffers     cached
Mem:       1539372     825648     713724          0      22976     244116
-/+ buffers/cache:     558556     980816
Swap:      4000144          0    4000144

```


Note that I have given a sync and swapoff and swapon about an hour ago. Curious. What are you looking for in this list that is related to the size of mythfrontend or mythwelcome?

---

### Post by My Name on 2010-04-28
Isn't the system designed to use as much memory as possible? or am I wrong...

---

### Post by lennardw on 2010-04-28
Yes a Linux system uses all the memory it can (which is good), but there is a diffirence between active memory and cached (inactive) memory.
The sizes I am referring to are active memory sizes. It is at any rate not good if a box starts pagina memory to disk.

---

### Post by My Name on 2010-04-28
okydoke

---

### Post by tgm4883 on 2010-04-28
I'd be interested in the memory usage statistics from when you think it is swapping.

---

### Post by lennardw on 2010-04-28
It's getting a little late here.. I'll record something tomorow and show you those stats when it is swapping.
The mythfrontend will be using approximately 700 - 800MB of RAM then.

---

### Post by tgm4883 on 2010-04-28
> **lennardw said:**
> It's getting a little late here.. I'll record something tomorow and show you those stats when it is swapping.
The mythfrontend will be using approximately 700 - 800MB of RAM then.

Great, would love to see that. Thanks.

---

### Post by lennardw on 2010-04-29
Here are some stats. I installed sysstat and left it running, so that I can get some proper statistics. As you can see, my box was swapping (just a tiny bit) around 11.45.

And the memory load was above the amount of RAM in my box at about 14.00 today. Today was far less 'swappy' then yesterday.

Does anyone know how to get the sar output in 24h time btw? - UPDATE Never mind about this one. I found the LC_@@@ variables.



free
```

lennard@wynne:~$ date
Thu Apr 29 23:46:10 CEST 2010
lennard@wynne:~$ free
             total       used       free     shared    buffers     cached
Mem:       1539372    1391868     147504          0      20156     248632
-/+ buffers/cache:    1123080     416292
Swap:      4000144      68644    3931500

```
ps aux --sort size |tail
```

lennard@wynne:~$ date
Thu Apr 29 23:46:15 CEST 2010
lennard@wynne:~$ ps aux --sort size |tail
www-data  2287  0.0  0.4 207128  7608 ?        S    Apr28   0:02 /usr/sbin/apache2 -k start
www-data  2286  0.0  0.4 207252  7376 ?        S    Apr28   0:03 /usr/sbin/apache2 -k start
www-data  2289  0.0  0.5 207920  8344 ?        S    Apr28   0:08 /usr/sbin/apache2 -k start
www-data  2288  0.0  0.5 208176  8380 ?        S    Apr28   0:02 /usr/sbin/apache2 -k start
lennard  11226  0.1  1.1 352804 17232 ?        SNsl 13:01   0:51 /usr/bin/mtd -d
syslog     892  0.0  0.0 125860   984 ?        Sl   Apr28   0:00 rsyslogd -c4
mysql     1563  0.2  2.1 286408 33308 ?        Sl   Apr28   3:21 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --user=mysql --pid-file=/var/run/mysqld/mysqld.pid --socket=/var/run/mysqld/mysqld.sock --port=3306
mythtv    2520  0.0  2.0 607288 31804 ?        Sl   Apr28   1:02 /usr/bin/mythbackend --logfile /var/log/mythtv/mythbackend.log
lennard   2380  0.1 15.2 635160 234716 ?       Sl   Apr28   1:35 mythwelcome
lennard  13844  8.5 41.0 1135000 631492 ?      Sl   16:30  36:44 /usr/bin/mythfrontend.real

```
sar -s 11:00:00 -e 16:00:00
```


lennard@wynne:~$ sar -s 11:00:00 -e 16:00:00
Linux 2.6.31-20-generic (wynne)         04/29/2010      _x86_64_        (4 CPU)

11:05:01 AM     CPU     %user     %nice   %system   %iowait    %steal     %idle
11:15:01 AM     all      1.77      0.11      1.20      0.24      0.00     96.67
11:25:01 AM     all      0.32      0.12      0.39      0.36      0.00     98.81
11:35:01 AM     all      1.66      0.12      1.14      0.29      0.00     96.79
11:45:01 AM     all      1.90     13.99      2.52      3.93      0.00     77.65
11:55:01 AM     all      6.12      7.56      1.96      1.66      0.00     82.70
12:05:01 PM     all     11.35      0.09      2.69      0.62      0.00     85.26
12:15:01 PM     all     10.94      0.07      2.58      0.49      0.00     85.92
12:25:01 PM     all     10.97      0.09      2.65      0.59      0.00     85.70
12:35:01 PM     all      9.89      0.08      2.44      1.28      0.00     86.31
12:45:01 PM     all     11.66      0.09      2.80      0.22      0.00     85.23
12:55:01 PM     all      9.48      0.19      2.64      2.52      0.00     85.18
01:05:02 PM     all      3.79      0.65      3.23      9.13      0.00     83.21
01:15:01 PM     all      3.20      0.01      2.19     23.20      0.00     71.40
01:25:02 PM     all      4.60      0.01      4.25     21.82      0.00     69.32
01:35:01 PM     all      2.85      0.01      2.85     22.78      0.00     71.51
01:45:01 PM     all      2.84      0.01      2.32     13.64      0.00     81.19
01:55:01 PM     all      3.52      0.00      1.72      8.20      0.00     86.56
02:05:01 PM     all      6.41      0.00      3.61      3.60      0.00     86.37
02:15:01 PM     all      1.82      0.00      3.27      4.94      0.00     89.96
02:25:01 PM     all      2.43      0.00      1.75     16.84      0.00     78.98
02:35:01 PM     all      9.36      0.00      3.31      8.62      0.00     78.71
02:45:01 PM     all      3.70      0.00      3.55      1.00      0.00     91.74
02:55:01 PM     all      1.23      0.00      2.40      0.26      0.00     96.11
03:05:01 PM     all      1.14      0.00      2.41      0.23      0.00     96.22
03:15:01 PM     all      2.00      0.00      1.70      7.46      0.00     88.84
03:25:01 PM     all      0.61      0.01      0.63      9.51      0.00     89.24
03:35:01 PM     all      0.57      0.00      0.61      9.53      0.00     89.29
03:45:01 PM     all      0.64      0.00      0.76     14.27      0.00     84.32
03:55:01 PM     all      0.67      0.00      0.88     18.35      0.00     80.09
Average:        all      4.41      0.81      2.23      7.09      0.00     85.46

```
sar -s 11:00:00 -e 16:00:00 -W
```


lennard@wynne:~$ sar -s 11:00:00 -e 16:00:00 -W
Linux 2.6.31-20-generic (wynne)         04/29/2010      _x86_64_        (4 CPU)

11:05:01 AM  pswpin/s pswpout/s
11:15:01 AM      0.00      0.00
11:25:01 AM      0.00      0.00
11:35:01 AM      0.01      0.00
11:45:01 AM      0.14     28.68
11:55:01 AM      7.26      3.76
12:05:01 PM      0.07      0.53
12:15:01 PM      0.00      0.00
12:25:01 PM      0.01      0.00
12:35:01 PM      0.29      0.00
12:45:01 PM      0.00      0.00
12:55:01 PM      2.02      0.00
01:05:02 PM      0.72      0.05
01:15:01 PM      1.88      0.00
01:25:02 PM      0.16      0.00
01:35:01 PM      0.12      0.00
01:45:01 PM      0.04      0.00
01:55:01 PM      0.00      0.00
02:05:01 PM      0.17      0.00
02:15:01 PM      0.00      0.00
02:25:01 PM      0.37      0.00
02:35:01 PM      0.00      0.00
02:45:01 PM      0.00      0.00
02:55:01 PM      0.01      0.00
03:05:01 PM      0.00      0.00
03:15:01 PM      0.03      0.00
03:25:01 PM      0.01      0.00
03:35:01 PM      0.00      0.00
03:45:01 PM      0.00      0.00
03:55:01 PM      0.00      0.00
Average:         0.46      1.15

```
sar -s 11:00:00 -e 16:00:00 -r
```


lennard@wynne:~$ sar -s 11:00:00 -e 16:00:00 -r
Linux 2.6.31-20-generic (wynne)         04/29/2010      _x86_64_        (4 CPU)

11:05:01 AM kbmemfree kbmemused  %memused kbbuffers  kbcached  kbcommit   %commit
11:15:01 AM     12348   1527024     99.20     25048    556292   1438132     25.96
11:25:01 AM     14476   1524896     99.06     25092    556164   1442032     26.03
11:35:01 AM     12976   1526396     99.16     25120    561704   1454580     26.26
11:45:01 AM     13656   1525716     99.11       424    620100   1508380     27.23
11:55:01 AM     12932   1526440     99.16    222392    367304   1528348     27.59
12:05:01 PM     13360   1526012     99.13    318216    268244   1529700     27.61
12:15:01 PM     13328   1526044     99.13    342312    243056   1530364     27.63
12:25:01 PM     12768   1526604     99.17    348036    237024   1531004     27.64
12:35:01 PM    115652   1423720     92.49    226488    257856   1532032     27.66
12:45:01 PM     12812   1526560     99.17    344376    238440   1533136     27.68
12:55:01 PM    372656   1166716     75.79     34940    314468   1304956     23.56
01:05:02 PM     12904   1526468     99.16    325488    420124   1275436     23.02
01:15:01 PM     13344   1526028     99.13    365396    468776   1273816     23.00
01:25:02 PM     13524   1525848     99.12    452192    561640   1162968     20.99
01:35:01 PM     12484   1526888     99.19    467936    576952    986544     17.81
01:45:01 PM    454768   1084604     70.46      9700    581012   1008244     18.20
01:55:01 PM    332328   1207044     78.41     57268    581276   1283416     23.17
02:05:01 PM     12584   1526788     99.18    318116    376692   1548356     27.95
02:15:01 PM    877128    662244     43.02     10300    145860   1020484     18.42
02:25:01 PM    531360   1008012     65.48     13120    162392   1331700     24.04
02:35:01 PM    408212   1131160     73.48     25348    164292   1642368     29.65
02:45:01 PM     13908   1525464     99.10    427880    130236   1644092     29.68
02:55:01 PM     13020   1526352     99.15    443248    111476   1644468     29.69
03:05:01 PM     14020   1525352     99.09    442620    108776   1644268     29.68
03:15:01 PM    798824    740548     48.11      9684    222916   1027376     18.55
03:25:01 PM    791820    747552     48.56     11512    228216   1027072     18.54
03:35:01 PM    791572    747800     48.58     11552    228220   1028016     18.56
03:45:01 PM    791160    748212     48.61     11900    229288   1028756     18.57
03:55:01 PM    791324    748048     48.59     11816    229324   1028752     18.57
Average:       251078   1288294     83.69    183708    336142   1342717     24.24

```

---

### Post by lennardw on 2010-05-02
Anyone?

Not that it really matters much anymore. I'm using xbmc as a frontend now. (haven't seen it's usage above approx 130MB yet)

I'm curious as why the frontend needs to use such amounts of memory  though. Or am I the only one with this 'problem' ?

---

### Post by Ribs on 2010-06-12
> **lennardw said:**
> Or am I the only one with this 'problem' ?
You're not the only one.

My 1GB backend and frontend machine really struggles to do anything without swapping. It used to be a 2gb machine (moved the memory module to another system) and it coped well. It really doesn't work too well with 1gb, which is crazy, given what it's running. My memory usage is very similar to yours and I would like to find a fix.

I managed to save a metric ton of memory by turning off innodb in mysql (now uses about a third of it's original memory) and the same again in mysql after putting the threads down to reasonable levels, like so:
<IfModule mpm_prefork_module>
    StartServers          2
    MinSpareServers       2
    MaxSpareServers       3
    MaxClients           50
    MaxRequestsPerChild   0
</IfModule>

So now it's working a bit better and I can watch TV without swapspace now, but I'm wondering where mythtv is using all it's memory?

Anyone else have any ideas?

---

