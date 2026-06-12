---
title: "NFS performance vs samba, awful?"
date: 2010-06-16
forum: Networking &amp; Wireless
---

### Post by fearlsgroove on 2010-06-16
I'm running an Ubuntu 9.10 file server in a mixed environment, sharing the same folders with NFS, samba and netatalk. I've found that performance when copying to the NFS share is quite bad compared with SAMBA even given the same 2 machines.

For example, with a 10.04 client, copying to a 9.10 server, copying to an NFS mount:

```
$ time dd if=/dev/zero of=/media/work/testfile bs=512k count=500
500+0 records in
500+0 records out
262144000 bytes (262 MB) copied, 30.3789 s, 8.6 MB/s

real	0m30.480s
user	0m0.000s
sys	0m0.780s
```

vs copying to the same server, same directory via samba (smbfs):

```
$ time dd if=/dev/zero of=/media/smbtest/testfile bs=512k count=500
500+0 records in
500+0 records out
262144000 bytes (262 MB) copied, 9.33345 s, 28.1 MB/s

real	0m9.388s
user	0m0.000s
sys	0m1.920s
```

The NFS is shared like so:

```
/export/data	<ip address>/24(rw,fsid=0,sync,no_subtree_check)
/export/data/work	<ip address>/24(rw,sync,no_subtree_check)
```

And the fstab line looks like this:
```
<ip address>:/work	/media/work	nfs4 rw,sync	0   0
```

Any help would be appreciated! Also happy to provide more info if anyone would like to see something specific.

---

