---
title: "no access to dvd's created with camera"
date: 2010-06-17
forum: Multimedia Software
---

### Post by spezticle on 2010-06-17
So, i'm helping out a user who has a hitachi dvd cam. makes movies records them to dvd's.
but the permissions of the disk do not allow for anybody to open them?

I can gksu nautilus to find the permissions of the disk are set to "-1 - user #-1"

what is this about and how do i fix it so that i can read/copy/do anything with the disk without root permission?

the owner permissions are set by the camera, i'm assuming, because the actual disk creation has nothing to do with ubuntu at all.

---

### Post by spezticle on 2010-06-17
trying to make a copy of the dvd disk with gnomebaker run with root privelages, this is the output:```

Read  speed: 22160 kB/s (CD 125x, DVD 16x).
Write speed:  3324 kB/s (CD  18x, DVD  2x).
Capacity: 536592 Blocks = 1073184 kBytes = 1048 MBytes = 1098 prMB
Sectorsize: 2048 Bytes
Copy from SCSI (1,0,0) disk to file '/home/family/Desktop/gnomebaker.iso'
end:    536592
addr:        0 cnt: 64
Errno: 5 (Input/output error), read_g1 scsi sendcmd: no error
CDB:  28 00 00 00 A4 C0 00 00 40 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 12 00 00 00 00 11 00 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x11 Qual 0x00 (unrecovered read error) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 4.320s timeout 40s
readom: Input/output error. Cannot read source disk
readom: Retrying from sector 42176.
.................
```

the condition of the disk is fine. no scratches, etc.

---

