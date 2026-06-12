---
title: "Mythbuntu system locking up on disk IO"
date: 2011-03-29
forum: Mythbuntu
---

### Post by JasonEde on 2011-03-29
I'm not sure how much of this is myth related, but on my system with Mythbuntu 10.04 I keep having the system lock up when doing disk io operations.

I've a 1TB drive that is split into 2 partitions. One of them is the default ubuntu partition type which is ext4. The second partition where I've stored all the data/recordings etc is xfs.

This used to be occasional, but is happening all the time now. I've checked the volume for errors and nothing is being reported as wrong. I'm sure this is disk IO errors as can be seen from iostat below...

Things I can check look at?


jason@jason-desktop:~$ iostat -x 5 3
Linux 2.6.32-30-generic-pae (jason-desktop)     29/03/11        _i686_  (4 CPU)

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           1.16    0.03    0.83    7.17    0.00   90.81

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               4.91     8.05    5.00    4.58   343.06   154.43    51.91    17.23 1780.64  19.64  18.82

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.15    0.00    0.15   24.34    0.00   75.36

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               0.00     1.00    0.00   23.20     0.00   224.00     9.66   142.13 5287.72  43.10 100.00

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.15    0.00    0.15   56.51    0.00   43.20

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               0.00     5.00    0.00   26.00     0.00   223.20     8.58   141.01 6205.91  38.46 100.00

---

### Post by LowSky on 2011-03-29
> **JasonEde said:**
> I'm not sure how much of this is myth related, but on my system with Mythbuntu 10.04 I keep having the system lock up when doing disk io operations.

I've a 1TB drive that is split into 2 partitions. One of them is the default ubuntu partition type which is ext4. The second partition where I've stored all the data/recordings etc is xfs.

This used to be occasional, but is happening all the time now. I've checked the volume for errors and nothing is being reported as wrong. I'm sure this is disk IO errors as can be seen from iostat below...

Things I can check look at?


```
jason@jason-desktop:~$ iostat -x 5 3
Linux 2.6.32-30-generic-pae (jason-desktop)     29/03/11        _i686_  (4 CPU)

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           1.16    0.03    0.83    7.17    0.00   90.81

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               4.91     8.05    5.00    4.58   343.06   154.43    51.91    17.23 1780.64  19.64  18.82

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.15    0.00    0.15   24.34    0.00   75.36

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               0.00     1.00    0.00   23.20     0.00   224.00     9.66   142.13 5287.72  43.10 100.00

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.15    0.00    0.15   56.51    0.00   43.20

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               0.00     5.00    0.00   26.00     0.00   223.20     8.58   141.01 6205.91  38.46 100.00

```


please use quote tags. it makes things easier to read.

I took a sample of my system so you get an idea of a healthy system.

I'm betting your issue is actually a loose or bad sata cable. Sata cables have been know to be very brittle, I have even had SATA sockets crack with little resistance against them. Make sure your cable isn't taught or bending too much, especially from the connector. If you can switch connectors and cables. Its cheaper than replacing a hard drive and data

```

john@jpc-desktop:~$ iostat -x 5 3
Linux 2.6.35-28-generic (jpc-desktop) 	03/29/2011 	_x86_64_	(4 CPU)

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           1.93    3.59    0.49    0.56    0.00   93.43

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               0.61    35.04    1.78    2.48   123.47   300.11    99.38     0.05   10.91   3.16   1.35
sdb               0.01    10.66    0.20    0.20    60.04    86.95   364.62     0.00    7.66   5.98   0.24
sdc               0.00    16.56    0.28    0.27   101.50   134.69   428.43     0.00    7.35   5.82   0.32
sdd               0.00    18.83    0.15    0.46    46.96   154.33   329.05     0.01   12.46  10.26   0.63
sde               0.01     0.00    0.00    0.00     0.04     0.00    11.16     0.00    4.45   4.38   0.00

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.35    0.00    0.05    0.00    0.00   99.60

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00
sdb               0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00
sdc               0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00
sdd               0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00
sde               0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.35    0.00    0.10    0.35    0.00   99.21

Device:         rrqm/s   wrqm/s     r/s     w/s   rsec/s   wsec/s avgrq-sz avgqu-sz   await  svctm  %util
sda               0.00    16.00    0.40   38.40     3.20   435.20    11.30     0.30    7.68   0.67   2.60
sdb               0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00
sdc               0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00
sdd               0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00
sde               0.00     0.00    0.00    0.00     0.00     0.00     0.00     0.00    0.00   0.00   0.00

```

---

### Post by JasonEde on 2011-04-01
When my system is not locking up then that is pretty much how it looks too. It started being the odd one off it was doing this 'freezing' but has become more frequent.

I will open it up and check all the connections this weekend.

---

### Post by JasonEde on 2011-09-22
I think I've tracked down the root cause of my IO issues...

When it locks up a mysqladmin process list reveals lots of these sorts of queries that seem to take ages to run...

updating | DELETE FROM credits WHERE starttime >= ? AND starttime < ? AND chanid = ? |
updating | DELETE FROM program WHERE starttime >= ? AND starttime < ? AND chanid = ? 

Do I have a database problem, and if so suggestions on fixing it are welcome... I'll enable sloe query logging so I'll hopefully get more info...

---

### Post by ian dobson on 2011-09-23
Hi,

If you have enough memory, then increase the buffers allocated by mysql. On my big server I have setup mysql so that the table cache is abit larger than my on disk tables. This reduced the schedule time (in mythtv) to less than 0.5 seconds.

in  /etc/mysql/my.cnf
key_buffer              = 192M
key_buffer_size         = 400M


Regards
Ian Dobson

---

