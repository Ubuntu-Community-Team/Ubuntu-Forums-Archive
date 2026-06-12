---
title: "Mythbuntu 14.04 Memory Leak?"
date: 2014-12-30
forum: Mythbuntu
---

### Post by mike_c2 on 2014-12-30
I have Mythbuntu 14.04 installed with all updates. In the last two weeks or so, I have seen memory usage increase from the normal 600mb - 900mb to almost 4GB. See the memory usage below, this is with only the backend running. There seems to be a memory leak from a recent update. Output from top also listed below, which doesn't seem to show what is using all of the memory. Any help would be appreciated, thanks.

Dual core 2.85Ghz/4GB memory

xxxx@xxxx:~$ free -m
            total       used       free     shared    buffers     cached
Mem:          3848        661       3187         29         36        318
-/+ buffers/cache:        306       3542
Swap:         3989          0       3989
xxxx@xxxx:~$ free -m
            total       used       free     shared    buffers     cached
Mem:          3848       1945       1903         30         46       1531
-/+ buffers/cache:        367       3481
Swap:         3989          0       3989
xxxx@xxxx:~$ free -m
            total       used       free     shared    buffers     cached
Mem:          3848       3712        136         33        111       3098
-/+ buffers/cache:        503       3345
Swap:         3989          0       3989
xxxx@xxxx:~$

=======================================

xxx@xxxx:~$ top

top - 14:45:06 up 15:48,  2 users,  load average: 0.01, 0.02, 0.05
Tasks: 174 total,   2 running, 172 sleeping,   0 stopped,   0 zombie
%Cpu(s):  1.3 us,  0.7 sy,  0.0 ni, 97.8 id,  0.2 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:   3941200 total,  3471796 used,   469404 free,    21328 buffers
KiB Swap:  4085756 total,      288 used,  4085468 free.  3025848 cached Mem

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND     
 1655 mexxxx    20   0  102136  13176   7056 S   2.3  0.3   0:33.73 x11vnc      
 1499 root      20   0  246672  22668  15260 S   1.7  0.6   0:38.22 Xorg        
 2351 mexxxx    20   0  477180  13932   9528 S   0.7  0.4   0:00.93 xfce4-term+ 
 1251 mysql     20   0 1347712  88972   4804 S   0.3  2.3   0:35.18 mysqld      
 5098 cmexxxx    20   0   23668   1668   1168 R   0.3  0.0   0:00.24 top         
    1 root      20   0   33836   3012   1316 S   0.0  0.1   0:01.02 init        
    2 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kthreadd    
    3 root      20   0       0      0      0 S   0.0  0.0   0:00.20 ksoftirqd/0 
    5 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/0:+ 
    7 root      20   0       0      0      0 S   0.0  0.0   0:00.85 rcu_sched   
    8 root      20   0       0      0      0 S   0.0  0.0   0:01.06 rcuos/0     
    9 root      20   0       0      0      0 R   0.0  0.0   0:00.43 rcuos/1     
   10 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuos/2     
   11 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuos/3     
   12 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcu_bh      
   13 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/0     
   14 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcuob/1

---

### Post by kpatz on 2014-12-30
Use the ">" key when in top to change the sort column to the Mem% column.  Then the processes using the most memory will appear at the top of the list.

---

### Post by mike_c2 on 2014-12-31
kpatz,

I have sorted by the memory column, still wondering what is using all of the memory.

top - 10:31:38 up 1 day, 11:34,  4 users,  load average: 0.12, 0.08, 0.05
Tasks: 178 total,   1 running, 177 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.5 us,  0.7 sy,  0.0 ni, 98.8 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:   3941200 total,  3678380 used,   262820 free,    11024 buffers
KiB Swap:  4085756 total,     2196 used,  4083560 free.  3229204 cached Mem

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND    
 1251 mysql     20   0 1348528  92816   3908 S   0.0  2.4   1:21.31 mysqld     
 2265 mythtv    20   0 3858068  53684   9640 S   0.3  1.4  20:07.00 mythbackend
 1499 root      20   0  248932  22324  14112 S   0.7  0.6   3:33.06 Xorg       
 1655 mexxxx    20   0  102136  13040   6848 S   0.7  0.3  13:53.46 x11vnc     
 1772 mexxxx    20   0  430440  12980   7628 S   0.0  0.3   0:02.33 xfce4-panel
 2351 mexxxx    20   0  477168  12168   7492 S   0.0  0.3   0:04.74 xfce4-term+
 1496 root      20   0  280588  11684   6916 S   0.0  0.3   0:01.92 apache2    
 1781 mexxxx    20   0  493200  11504   4612 S   0.0  0.3   0:01.34 xfdesktop  
 3704 www-data  20   0  284380  10304   3132 S   0.0  0.3   0:00.31 apache2    
 1502 www-data  20   0  284308  10300   3300 S   0.0  0.3   0:00.26 apache2    
 3778 www-data  20   0  284364  10172   3000 S   0.0  0.3   0:00.58 apache2    
 3705 www-data  20   0  284028  10116   3360 S   0.0  0.3   0:00.39 apache2    
 3702 www-data  20   0  284304   9832   2740 S   0.0  0.2   0:00.18 apache2    
 3706 www-data  20   0  284252   9656   2764 S   0.0  0.2   0:00.11 apache2    
 1505 www-data  20   0  283660   9296   2948 S   0.0  0.2   0:00.13 apache2    
 1503 www-data  20   0  283644   9204   2864 S   0.0  0.2   0:00.13 apache2    
 3703 www-data  20   0  282728   9192   3656 S   0.0  0.2   0:00.33 apache2

---

### Post by kpatz on 2014-12-31
Mysqld is using 2.4% of your memory, and mythbackend 1.4%.  That's perfectly reasonable.

Try using htop instead of top.  htop gives a more accurate indication of memory used/free.  Top may show a lot of memory used, but that's because unused memory is used for file/disk caching.

If you don't have htop, use **sudo apt-get install htop** to install it.

---

### Post by mike_c2 on 2014-12-31
OK, I installed htop, I am still not sure why free -m shows a higher amount of memory used.

htop:

1  [||                        4.6%]     Tasks: 94, 135 thr; 3 running
  2  [||                        2.0%]     Load average: 0.05 0.09 0.07 
  Mem[||||||||||||||||||||449/3848MB]     Uptime: 1 day, 12:05:52
  Swp[|                     2/3989MB]

  PID USER      PRI  NI  VIRT   RES   SHR S CPU% MEM%   TIME+  Command
 1499 root       20   0  242M 22412 14200 S  2.0  0.6  3:41.74 /usr/bin/X -core
 1655 mexxxx     20   0   99M 13056  6864 S  2.0  0.3 14:02.43 x11vnc -rfbauth /
 8882 mexxxx      20   0 24492  2064  1440 R  1.3  0.1  0:00.30 htop
 8413 mexxxx      20   0 23672  1688  1180 S  0.7  0.0  0:03.48 top
 2272 mythtv     20   0 3767M 53684  9640 S  0.0  1.4  0:03.58 /usr/bin/mythback
 2351 mexxxx      20   0  466M 13000  7844 S  0.7  0.3  0:05.70 xfce4-terminal
 1251 mysql      20   0 1316M 94060  4660 S  0.0  2.4  1:22.82 /usr/sbin/mysqld
 1984 rtkit      21   1  164M  1240  1024 S  0.0  0.0  0:00.52 /usr/lib/rtkit/rt
 2724 mythtv     20   0 3767M 53684  9640 S  0.0  1.4  0:19.49 /usr/bin/mythback
 2265 mythtv     20   0 3767M 53684  9640 S  0.7  1.4 20:09.86 /usr/bin/mythback
 3314 mythtv     20   0 3767M 53684  9640 S  0.0  1.4  6:33.92 /usr/bin/mythback
 1301 mysql      20   0 1316M 94060  4660 S  0.0  2.4  0:02.14 /usr/sbin/mysqld
    1 root       20   0 33836  2844  1204 S  0.0  0.1  0:01.02 /sbin/init
  282 root       20   0 19608   832   516 S  0.0  0.0  0:00.21 upstart-udev-brid
  286 root       20   0 52092  1904   768 S  0.0  0.0  0:00.19 /lib/systemd/syst
  592 root       20   0  266M  4120  2668 S  0.0  0.1  0:02.30 smbd -F
F1Help  F2Setup F3SearchF4FilterF5Tree  F6SortByF7Nice -F8Nice +F9Kill  F10Quit

===================
free -m

xxxx@xxxx:~$ free -m
            total       used       free     shared    buffers     cached
Mem:          3848       1945       1903         30         46       1531
-/+ buffers/cache:        367       3481
Swap:         3989          0       3989

---

### Post by The Cog on 2014-12-31
Mike_c2:
Please use code tags, not quote tags (need to use the "advanced" editor to see a code button). It makes reading so much easier.

Your system seems to only be using around 10% of its RAM for programs. The rest is being used as disk cache, which doesn't do any harm. See this web site for an explanation:
[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

P.S.
You need to use **free -m --si** to see the usage in megabytes. With just **free -m**, it shows usage in mebibytes instead.

---

### Post by mike_c2 on 2014-12-31
Kpatz and Cog,

Thanks for your help, I have a better understanding about memory usage in Linux!

---

