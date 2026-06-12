---
title: "mdadm raid 1 slow"
date: 2012-12-03
forum: Networking &amp; Wireless
---

### Post by osa2 on 2012-12-03
hi all,

I have build myself a small nas as test.
It is using ubuntu server 12.10

The installation is done on a 4 GB usb stick (this I know is slow for boot)
2 hard-disks of 1 TB are being used as raid 1

When I test the local 

Here are some settings:

sudo mdadm --detail /dev/md0
[sudo] password for wim:
/dev/md0:
        Version : 1.2
  Creation Time : Tue Nov 27 17:00:51 2012
     Raid Level : raid1
     Array Size : 976631360 (931.39 GiB 1000.07 GB)
  Used Dev Size : 976631360 (931.39 GiB 1000.07 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent

    Update Time : Mon Dec  3 10:34:57 2012
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           Name : nas:0  (local to host nas)
           UUID : ebfa17a9:915551f4:e45384b8:59877a13
         Events : 19

    Number   Major   Minor   RaidDevice State
       0       8        0        0      active sync   /dev/sda
       1       8       16        1      active sync   /dev/sdb



Hdparm individual drives:

sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   8742 MB in  2.00 seconds = 4374.50 MB/sec
 Timing buffered disk reads: 516 MB in  3.00 seconds = 171.88 MB/sec

/dev/sdb:
 Timing cached reads:   8598 MB in  2.00 seconds = 4302.40 MB/sec
 Timing buffered disk reads: 396 MB in  3.01 seconds = 131.59 MB/sec


Hdparm for the raid set:

/dev/md0:
 Timing cached reads:   8538 MB in  2.00 seconds = 4272.31 MB/sec
 Timing buffered disk reads: 508 MB in  3.00 seconds = 169.14 MB/sec

Signaling of the sata interface

wim@nas:~$ sudo hdparm -I /dev/sda | grep -i speed
           *    Gen1 signaling speed (1.5Gb/s)
           *    Gen2 signaling speed (3.0Gb/s)
           *    Gen3 signaling speed (6.0Gb/s)


wim@nas:~$ sudo hdparm -I /dev/sdb | grep -i speed
           *    Gen1 signaling speed (1.5Gb/s)
           *    Gen2 signaling speed (3.0Gb/s)


Now, why is writing so slow to this setup?

When I write using samba share I get around 25Mb/s = around 180Mbps
The network is full gigabit and on my real server (other not ubuntu)  I get writing speeds of around 98Mb/s

When I test in linux it shows 340 MB/s

wim@nas:/mnt/DATA$ dd if=/dev/zero of=/mnt/DATA/out.img bs=8k count=256k
262144+0 records in
262144+0 records out
2147483648 bytes (2.1 GB) copied, 6.31609 s, 340 MB/s


SO, I think theoretical I can get 340 MB/s = fast enough this is about gigabit speed
so loosing half speed is what I should want to achief. around 100MB/s is enough.

But I only get 23. What can I see to adjust to get it better.

Ubuntu gots 8Gb of ram and 4core AMD FX 4100 3GHz CPU
Should all be fast enough.

Suggestions???
thanks.

FS= EXT4

---

### Post by osa2 on 2012-12-05
No one?
Or is it in the wrong group?

---

