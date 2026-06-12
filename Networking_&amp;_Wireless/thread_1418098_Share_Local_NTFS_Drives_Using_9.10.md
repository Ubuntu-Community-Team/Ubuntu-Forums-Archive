---
title: "Share Local NTFS Drives Using 9.10"
date: 2010-02-28
forum: Networking &amp; Wireless
---

### Post by wdavro on 2010-02-28
I have a computer that's booting Ubuntu 9.10 from the first of 4 drives.  The other 3 drives are formatted as NTFS.  Is it possible for my 9.10 to share the NTFS drives to the network so my other network users can access my NTFS drives while I'm booted to 9.10?

---

### Post by johnson.d on 2010-03-01
Yes, You can share the NTFS drives among the network.You can mount an NTFS partition using the following command:

```
$ sudo mount -t ntfs /dev/<dev-name> /<mount-point>
```

You can make the mounting permanent by adding the following line to the /etc/fstab file:

```
/dev/<dev-name> /<mount-point> ntfs defaults 0 0
```

If the drive is mounted as a Read-Only file system, it could be because of lack of NTFS write support. You can use the following command to add write support for NTFS

```
$ sudo apt-get install ntfs-3g
```

After mounting the partition, sharing such a mounted drive is no different from sharing any folder on the file system.

You can use the following procedure to share it in the network through samba using Nautilus:

1) Browse through the folders to get the view of the folder where the drive is mounted.
2) Right click on the folder and click share.
3) A window will open, click on the Share tab.
4) Check "Share this folder". You can check the other boxes as per your need.
5) Click "Create share"

Now you can browse the share from other machines.

If all your client machines are running Linux, you may also consider using NFS for sharing.

---

### Post by wdavro on 2010-03-03
Excellent!  Solved the problem exactly.

Thank you very much, Johnson.d

---

