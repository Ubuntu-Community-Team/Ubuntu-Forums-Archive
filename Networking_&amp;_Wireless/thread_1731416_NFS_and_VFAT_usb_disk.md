---
title: "NFS and VFAT usb disk"
date: 2011-04-17
forum: Networking &amp; Wireless
---

### Post by warp4ever on 2011-04-17
Where do I go wrong?

**SERVER:**

mounted usb/ext3 disk:
```
LABEL=mmedia            /net/mmedia        ext3    defaults,auto   0       0
```

and usb/vfat disk mounted as:
```
LABEL=Elements          /net/Beatles       vfat    uid=naam,gid=naam,iocharset=utf8  0 0
```

Permissions:
```
drwxr-xr-x 10 naam naam      32K 1970-01-01 01:00 Beatles
drwxrwxrwx 13 naam users    4.0K 2011-04-15 01:03 mmedia
```

Then I made the Beatles disk visable in the music map by symlink:

```
ln -s /net/beatles /net/mmedia/music/Beatles
```

Permissions:
```
lrwxrwxrwx   1 naam naam      17 2011-04-17 12:21 Beatles -> /net/Beatles
```

dirlist /net/mmedia/music/Beatles:
```
...
drwxr-xr-x 16 naam naam  32K 2008-12-15 23:51 Beatles
drwxr-xr-x 14 naam naam  32K 2008-11-28 05:59 Beatles - Apple records
drwxr-xr-x 30 naam naam  32K 2008-11-28 06:58 Beatles solo
drwxr-xr-x  7 naam naam  32K 2008-11-28 06:16 Beatles Tribute
....

```
To make both drives visable to NFS clients on the network:

/etc/exports:

```
/net/mmedia        10.0.0.0/24(rw,no_subtree_check)
/net/Beatles       10.0.0.0/24(ro,no_subtree_check)

```
-----------------------------

**CLIENT:**

/etc/fstab
```
10.0.0.12:/net/mmedia      /media/mmedia   nfs     defaults        0       0
```

Dirlists:
/media
```
drwxrwxrwx 13 naam users    4,0K 2011-04-15 01:03 mmedia
```
..
/media/mmedia
```
drwxrwxr-x 144 naam naam 4,0K 2011-04-17 12:21 music
```
..
/media/mmedia/music
```
lrwxrwxrwx   1 naam naam     17 2011-04-17 12:21 Beatles -> /net/Beatles
```
..
/net/mmedia/music/Beatles
```
lrwxrwxrwx 1 naam naam 17 2011-04-17 12:21 Beatles -> /netdrive/Beatles
```

[SIZE="3"]The contents of this map remains not visable on the client![/SIZE]

---

