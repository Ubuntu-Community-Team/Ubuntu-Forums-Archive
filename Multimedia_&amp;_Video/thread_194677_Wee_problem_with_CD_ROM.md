---
title: "Wee problem with CD ROM"
date: 2006-06-11
forum: Multimedia &amp; Video
---

### Post by darrenst on 2006-06-11
Hi folks.

I've found that I can copy discs burned in Ubuntu no problem. But discs I have burned using Windows are a problem.

The GUI seems to hang for ages. But I have found out that behind the scenes, this is the command that is causing grief.

It basically runs very quickly to the end of the disk, but then hangs for ages on one of the very last sectors.

darren@ubuntu-desktop:~$ readcd -dev=/dev/hdc -f=/home/darren/CopyCD/Ubuntu_6.06_i386.iso
Read  speed:  7056 kB/s (CD  40x, DVD  5x).
Write speed:  5644 kB/s (CD  32x, DVD  4x).
Capacity: 357297 Blocks = 714594 kBytes = 697 MBytes = 731 prMB
Sectorsize: 2048 Bytes
Copy from SCSI (1,0,0) disk to file '/home/darren/CopyCD/Ubuntu_6.06_i386.iso'
end:    357297
readcd: Success. read_g1: scsi sendcmd: no error
CDB:  28 00 00 05 73 80 00 00 31 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: F0 00 03 00 05 73 B0 0E 00 00 00 00 11 05 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x11 Qual 0x05 (l-ec uncorrectable error) Fru 0x0
Sense flags: Blk 357296 (valid)
resid: 100352
cmd finished after 5.918s timeout 40s
readcd: Success. Cannot read source disk
readcd: Retrying from sector 357248.
.................................................~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~
readcd: Success. Error on sector 357296 not corrected. Total of 1 errors.

Time total: 1067.641sec
Read 714496.00 kB at 669.2 kB/sec.
Max corected retry count was 0 (limited to 128).
The following 1 sector(s) could not be read correctly:
357296
darren@ubuntu-desktop:~$

Any thoughts?

Cheers,

Darren

---

