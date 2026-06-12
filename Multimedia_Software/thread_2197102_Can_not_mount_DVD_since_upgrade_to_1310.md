---
title: "Can not mount DVD since upgrade to 13:10"
date: 2014-01-02
forum: Multimedia Software
---

### Post by jonathan-l-harrison on 2014-01-02
I had to rebuild my wife's laptop HP Pavillion g series, as it would not upgrade to latest version of Ubuntu, 13:10 and ended braking it.  All is sorted now except for playing DVDs.  Done all the usual installing Ubuntu extras etc.  but still will not play.  I am getting this message:

```
Error mounting /dev/sr0 at /media/chiara/OVER_THE_HEDGE: Command-line `mount -t "udf" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,iocharset=utf8,umask=0077" "/dev/sr0" "/media/chiara/OVER_THE_HEDGE"' exited with non-zero exit status 32: mount: block device /dev/sr0 is write-protected, mounting read-onlymount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

And dmesg | tail -n5 gives me:
```
 dmesg | tail -n5[ 1029.691821] Read(10): 28 00 00 00 02 70 00 00 01 00
[ 1029.691836] end_request: I/O error, dev sr0, sector 2496
[ 1029.691912] UDF-fs: error (device sr0): udf_read_tagged: read failed, block=512, location=512
[ 1029.691921] UDF-fs: warning (device sr0): udf_load_vrs: No anchor found
[ 1029.691925] UDF-fs: warning (device sr0): udf_fill_super: No partition found (1)

```

Any ideas please?

---

