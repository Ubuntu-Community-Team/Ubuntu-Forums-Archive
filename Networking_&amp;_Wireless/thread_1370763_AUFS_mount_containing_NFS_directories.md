---
title: "AUFS mount containing NFS directories"
date: 2010-01-02
forum: Networking &amp; Wireless
---

### Post by jgbc123 on 2010-01-02
If I try to mount the AUFS filesystem from a nfs and local directory in Ubuntu 9.10 like this:

```

sudo mount -t aufs br=/mnt/nfs=rw:/home/data/local=ro none /mnt/union

```

I get segmentation fault and my system crashes: 

```

comm: file 2 is not in sorted order
mount: block device none is write-protected, mounting read-only
Segmentation fault
Killed
/sbin/mount.aufs: bad /proc/3709/mounts

```

In 9.04 the same mount command worked fine using unionfs.

Am I doing something wrong or is it a bug?

---

### Post by jgbc123 on 2010-04-04
I found a workaround that kind of works. I changed from nsf to smb, and now aufs works most of the time. I added the following to fstab:

```

//readynas/media   /mnt/media      cifs	      iocharset=utf8,codepage=unicode,unicode,uid=1000,gid=2000,user=smb,password=xxxx,file_mode=0644,dir_mode=0755     0       0
#unionfs           /mnt/union      unionfs       dirs=/mnt/media=rw:/home/data/=ro                 0       0
aufs               /mnt/photos     aufs          br:/mnt/media/Photos=rw:/home/data/Photos=ro      0       0

```

But occasionally the filesystem stops working, and I get the following error in my syslog:

```
 
Apr  4 14:33:23 aladdin kernel: [20243.343467] aufs au_wh_test:96:f-spot[5244]: I/O Error, .wh.20080607-o004541-jb00l.jpg Invalid whiteout entry type 040755.

```

Any ideas on what is wrong? Is aufs just buggy???

---

### Post by GioF_71 on 2010-05-17
> **jgbc123 said:**
> I found a workaround that kind of works. I changed from nsf to smb, and now aufs works most of the time. I added the following to fstab:

```

//readynas/media   /mnt/media      cifs	      iocharset=utf8,codepage=unicode,unicode,uid=1000,gid=2000,user=smb,password=xxxx,file_mode=0644,dir_mode=0755     0       0
#unionfs           /mnt/union      unionfs       dirs=/mnt/media=rw:/home/data/=ro                 0       0
aufs               /mnt/photos     aufs          br:/mnt/media/Photos=rw:/home/data/Photos=ro      0       0

```

But occasionally the filesystem stops working, and I get the following error in my syslog:

```
 
Apr  4 14:33:23 aladdin kernel: [20243.343467] aufs au_wh_test:96:f-spot[5244]: I/O Error, .wh.20080607-o004541-jb00l.jpg Invalid whiteout entry type 040755.

```

Any ideas on what is wrong? Is aufs just buggy???


The same has happened to me too. I don't like to mount a samba share on linux because of the "secret" file with plain text password.
I successfully tried i-scsi instead, but it's a bit hard to handle properly startup and shutdown (automatic mount on startup & clean shutdown), I am still investigating.

---

