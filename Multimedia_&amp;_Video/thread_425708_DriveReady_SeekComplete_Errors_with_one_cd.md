---
title: "DriveReady SeekComplete Errors with one cd"
date: 2007-04-27
forum: Multimedia &amp; Video
---

### Post by Sohum on 2007-04-27
Firstly, my CD Drive works perfectly with every other CD I have tried. 
I have this one CD: it is a burnt Audio CD from much earlier. It works fine on standalone CD Players like my car CD player and my LG HD and DVD recorder, but whenever I put it into my Linux box it gives fails to mount. 
```
sohum@h2g2v2 pts/1:4613 ~% dmesg | tail
[ 5122.632000] ide: failed opcode was: unknown
[ 5122.636000] hda: error code: 0x70  sense_key: 0x05  asc: 0x64  ascq: 0x00
[ 5122.636000] end_request: I/O error, dev hda, sector 64
[ 5122.636000] isofs_fill_super: bread failed, dev=hda, iso_blknum=16, block=16
[ 5190.148000] hda: command error: status=0x51 { DriveReady SeekComplete Error }
[ 5190.148000] hda: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[ 5190.148000] ide: failed opcode was: unknown
[ 5190.148000] hda: error code: 0x70  sense_key: 0x05  asc: 0x64  ascq: 0x00
[ 5190.148000] end_request: I/O error, dev hda, sector 64
[ 5190.152000] isofs_fill_super: bread failed, dev=hda, iso_blknum=16, block=16

```
The CD is fine, as it plays elsewhere. The drive is fine, as it reads other CDs.  It's only the combination of the two that seems to not work?

---

