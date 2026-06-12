---
title: "slow transfer rate between 2 gigabit devices"
date: 2011-03-02
forum: Networking &amp; Wireless
---

### Post by gettons on 2011-03-02
Hi all,


First sorry for the very *general* matter, but unfortunately this is the problem I am facing at the moment.

I am struggling trying to understand the reason for a fairly slow data transfer rate between two machines. ( tried point to point and also via a 1 gb switch )
One is nfs/http/ftp server ( with raid1 and lvm on top ), the other one my desktop pc.
Both OS with default options, no changes to kernel in proc or other sort of thing.



[COLOR="Red"]Hardware is full recognized and perfectly working:[/COLOR]
The server has 4gb ram, Intel Core 2 Duo CPUE6850 @ 3.00GHz, 1000Mb/s NIC card and Lucid 10.04 64 bit, 250Giga Hard disk.
The client has 3gb ram, Intel Core 2 CPU 6320  @ 1.86GHz, 1000Mb/s NIC card and Ubuntu Maverick 32bit , 150Gb Hard disk.


[COLOR="Red"]Raw data is good:[/COLOR]
gettons@gettons-desktop:~$ iperf -c MYSERVER
------------------------------------------------------------
Client connecting to MYSERVER, TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  3] local 192.168.3.4 port 48906 connected with 192.168.3.2 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec  1.09 GBytes    938 Mbits/sec


[COLOR="Red"]Tests on the local disk:[/COLOR]
root@MYSERVER:~# bonnie++ -d /mnt/ -r `free -m | grep 'Mem:' | awk '{print $2}'` -s $(echo "scale=0;`free -m | grep 'Mem:' | awk '{print $2}'`*2" | bc -l) -u gettons
Using uid:1000, gid:1000.
Writing a byte at a time...done
Writing intelligently...done
Rewriting...done
Reading a byte at a time...done
Reading intelligently...done
start 'em...done...done...done...done...done...
Create files in sequential order...done.
Stat files in sequential order...done.
Delete files in sequential order...done.
Create files in random order...done.
Stat files in random order...done.
Delete files in random order...done.
Version  1.96       ------Sequential Output------ --Sequential Input- --Random-
Concurrency   1     -Per Chr- --Block-- -Rewrite- -Per Chr- --Block-- --Seeks--
Machine        Size K/sec %CP K/sec %CP K/sec %CP K/sec %CP K/sec %CP  /sec %CP
MYSERVER     7888M   754  97 64825   9 31211   4  3479  88 102054   5 258.5   2
Latency             15626us    4693ms    2346ms   52158us     102ms     236ms
Version  1.96       ------Sequential Create------ --------Random Create--------
MYSERVER           -Create-- --Read--- -Delete-- -Create-- --Read--- -Delete--
              files  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP  /sec %CP
                 16 18344  25 +++++ +++ +++++ +++ +++++ +++ +++++ +++ +++++ +++
Latency               254us     568us     430us     262us      30us      40us
1.96,1.96,MYSERVER,1,1299098739,7888M,,754,97,64825,9,31211,4,3479,88,102054,5,258.5,2,16,,,,,18344,25,+++++,+++,+++++,+++,+++++,+++,+++++,+++,+++++,+++,15626us,4693ms,2346ms,52158us,102ms,236ms,254us,568us,430us,262us,30us,40us


[COLOR="Red"]Again, tests on the local disk:[/COLOR]
root@MYSERVER:/mnt# date && dd if=/dev/zero of=ddfile bs=1M count=7888 && sync && date
Wed Mar  2 20:54:22 GMT 2011
7888+0 records in
7888+0 records out
8271167488 bytes (8.3 GB) copied, 113.39 s, 72.9 MB/s
Wed Mar  2 20:56:27 GMT 2011

[COLOR="Red"]Write over nfs3 default options from desktop to server :[/COLOR]
root@gettons-desktop:/mnt# date && dd if=/dev/zero of=ddfile bs=1M count=6030 && sync && date
Wed Mar  2 21:00:23 GMT 2011
6030+0 records in
6030+0 records out
6322913280 bytes (6.3 GB) copied, 179.152 s, 35.3 MB/s
Wed Mar  2 21:03:22 GMT 2011



[COLOR="Red"]Conclusion:[/COLOR]
Read speed with http, ftp, nfsv3 are 55~60 MB/s
I am not expecting 100MB/s but a good 80 maybe yes.




Thanks in advance

---

