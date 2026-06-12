---
title: "Ipod nano 6th doesn't mount in ubuntu 11.04"
date: 2011-05-11
forum: Multimedia Software
---

### Post by bako on 2011-05-11
Hi all.
i've just bought an Ipod nano 6th.
i managed the music from mac osx on the macbook pro and it was fine.
now i tried with my home pc that is an ubuntu 11.04.
the problem is that the ipod is recognized (it is in the left bar in nautilus) but it it not monted.

this is the error

```

Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdb2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

this is the log.

```

 dmesg | tail 
[ 4867.484362] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 4867.509855]  sdb: [mac] sdb1 sdb2
[ 4867.513113] sd 6:0:0:0: [sdb] 1926080 4096-byte logical blocks: (7.88 GB/7.34 GiB)
[ 4867.515375] sd 6:0:0:0: [sdb] No Caching mode page present
[ 4867.515383] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 4867.515388] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[ 4867.992068] sd 6:0:0:0: [sdb] Bad block number requested
[ 4867.992107] hfs: unable to find HFS+ superblock
[ 4868.152066] sd 6:0:0:0: [sdb] Bad block number requested
[ 4868.152195] hfs: unable to find HFS+ superblock


```

---

### Post by slickytail on 2011-05-17
pretty much the same for me, but im using ipod nano 5th.

---

### Post by wolfen69 on 2011-05-17
My ipod touch doesn't work after a clean install of xubuntu 11.04

I have all the needed files as far as I know. It worked in 10.10, weird.

---

### Post by RedOctober17 on 2011-05-22
I've got the same issue, it's a known bug in 11.04

[https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/734883](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/734883)

So far no solutions that I can find. What bugs me most is that even though it won't mount, the iPod says it's connected, and the only way to disconnect I've found is to go into the disk manager and "power down" that drive. Of course, this means it won't charge, unless I plug it back in so it's once more "connected" without mounting.

---

### Post by dfarrell07 on 2011-10-14
Just read the entire bug report. There seems to be a solution now. It is in comment 42, linked here: [http://bit.ly/ni7YUK](http://bit.ly/ni7YUK)

I'm upgrading to 11.10 now, so I can't try that fix, but I'll post back if 11.10 fixed this issue for me.

---

### Post by dfarrell07 on 2011-10-14
For me, upgrading to 11.10 fixed all issues with a 16GB iPod Nano 6th Generation. It mounts with no errors.

---

