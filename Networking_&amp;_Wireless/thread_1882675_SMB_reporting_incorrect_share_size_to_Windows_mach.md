---
title: "SMB reporting incorrect share size to Windows machines?"
date: 2011-11-17
forum: Networking &amp; Wireless
---

### Post by pentas on 2011-11-17
Just finished setting up a system with 4x3TB drives in RAID 6, and the system properly recognizes the total drive size of 6TB (which is correct).  The entirety of this array is being shared to Windows systems over samba.

Windows systems *should* be recognizing this share as ~5.46 TiB as Windows uses TiB rather than TB, however the Windows systems are recognizing it as 5.37 TiB.  Note, that there is no reserved space on the partition and this is the *total* size of the drive, not free space.  Also, the root partition for the OS is on a separate drive, so this share is only for data storage.

Any idea why there's a discrepancy or how I can fix this?

---

### Post by pentas on 2011-11-17
Just did some more research, and found something interesting:

```
 $> df -H
/dev/md0      6.0T      195M     6.0T    1%    /data
``````
 $> df -h
/dev/md0      5.4T      186M     5.4T    1%    /data
```Perhaps it's not samba (directly), but something in the way the OS is reporting the free space?  Any ideas?

---

