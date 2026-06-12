---
title: "DVD+RW Cannot Mount in Ubuntu 7.10"
date: 2007-10-30
forum: Multimedia &amp; Video
---

### Post by DeadToad on 2007-10-30
I have a Sony Vaio laptop (6 years old) with a DVD-ROM drive.

I have WinXP on one partition, and Ubuntu Gutsy Gibbon 7.10 on another.

In XP, I can mount and read CD, CD-R, DVD, DVD+RWs fine.

In Gutsy, I can mount  and read CD, CD-R, DVDs fine.
I cannot mount a DVD+RW or read it.

Does anyone have any suggestions?
Thanks.
DeadToad

---

### Post by DeadToad on 2007-11-04
i still can't mount my mule!
HELP!!!!!!!! :!:

---

### Post by shane.reid on 2007-11-05
I have this issue as well - I'm a pretty seasoned Ubuntu user and did a clean install on a new laptop for Gutsy and had my previous data backed up on a DVD+RW that i burned on a windows desktop...

Gutsy wont mount it but a windows pc will mount it fine.

shane@azeroth:~$ sudo mount -t udf /dev/dvd /mnt/
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


shane@azeroth:~$ dmesg | tail
[ 5552.812000] end_request: I/O error, dev sr0, sector 240196
[ 5552.816000] end_request: I/O error, dev sr0, sector 240204
[ 5552.820000] end_request: I/O error, dev sr0, sector 240236
[ 5552.820000] end_request: I/O error, dev sr0, sector 240260
[ 5552.824000] end_request: I/O error, dev sr0, sector 240268
[ 5552.828000] end_request: I/O error, dev sr0, sector 1179776
[ 5552.900000] end_request: I/O error, dev sr0, sector 256
[ 5596.096000] UDF-fs: No fileset found
[ 5596.180000] Unable to identify CD-ROM format.
[ 5665.712000] UDF-fs: No fileset found

---

### Post by DeadToad on 2007-11-06
shane.reid,
It looks like this may be a "Gutsy" or "Ubuntu" issue, since we can read all other formats, even in Windoze.
Maybe soon we'll have a 'fix' for this issue.
Regarding your problem, I would go back to Windoze, and burn that DVD+RW to CD-Rs, so I could mount it in Ubuntu and recover that data.
That's what I finally had to do.  It was inconvenient, but my only option, other than copying all that data to a USB flash drive, which would have worked, also.
Good day.
DeadToad

---

### Post by shane.reid on 2007-11-07
> **DeadToad said:**
> shane.reid,
It looks like this may be a "Gutsy" or "Ubuntu" issue, since we can read all other formats, even in Windoze.
Maybe soon we'll have a 'fix' for this issue.
Regarding your problem, I would go back to Windoze, and burn that DVD+RW to CD-Rs, so I could mount it in Ubuntu and recover that data.
That's what I finally had to do.  It was inconvenient, but my only option, other than copying all that data to a USB flash drive, which would have worked, also.
Good day.
DeadToad

It is definitively an issue - I can mount and read this DVD in my XP VMware - but not in ubuntu which is the Host OS for my VMware.

---

### Post by bss on 2007-11-07
Please post your /etc/fstab file.
```
cat /etc/fstab #for terminal sysem..
```

sometimes anoter device is mounted where CDROM should be.

---

