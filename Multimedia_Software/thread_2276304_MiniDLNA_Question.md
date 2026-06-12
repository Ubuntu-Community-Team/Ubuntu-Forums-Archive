---
title: "MiniDLNA Question"
date: 2015-05-01
forum: Multimedia Software
---

### Post by AnotherKevin on 2015-05-01
Hi All!

I have MiniDLNA set up in my Kubuntu 15.04 partition.  All of my video and music files are on my Win7 partition.  Is it possible to point MiniDLNAA to my windows partition to serve up my media? Or does it have to be on the same partition.

Thanks!

Kevin

---

### Post by SeijiSensei on 2015-05-01
You can have Linux [mount your Windows partition at boot]("https://help.ubuntu.com/community/MountingWindowsPartitions").

You can also do it manually.  First, let's create a "mount point," which is nothing more than an empty directory. 
```
sudo mkdir /media/windows
```

Now let's mount your Windows partition.  First, we need to find it, which is most easily accomplished with blkid:
```
sudo blkid
```
Find the one that has 'TYPE="ntfs"'; on my machine that's called /dev/sda2:
```
/dev/sda2: UUID="7BD7EBD65436CD44" TYPE="ntfs" 
```

Now let's mount it to /media/windows:
```
sudo mount /dev/sda2 /media/windows
```

The linked article tells you how to make all this happen automatically by editing /etc/fstab. There you should use the "UUID" to uniquely identify the partition as described.

Since you just want to distribute the files with DLNA, you might consider using "ro" ("read-only") in the options list in /etc/fstab.  That will protect you against any accidental damage to the Windows file system.  If you intend to write files there from Ubuntu, you'll need to use "rw" ("read-write") instead of course.

---

