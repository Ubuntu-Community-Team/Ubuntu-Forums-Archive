---
title: "Nautilus no longer provides SMB mount points in ~/.gvfs"
date: 2010-10-29
forum: Networking &amp; Wireless
---

### Post by taiyal on 2010-10-29
in Ubuntu 10.04, SMB network shares mounted through Nautilus could be found with mount points in ~/.gvfs/ . However, since upgrading to Ubuntu 10.10, I can no longer find those mount points in that location.

Did the location of the mount points move, or does Nautilus now manage SMB entirely through its own means rather than giving the shares a filesystem mount point?  And if so, is there any way to revert Nautilus' behavior to that in 10.04?


The underlying problem here is that Ubuntu's GUI method of mounting SMB shares makes them generally inaccessible to most other applications, and the problem now is that the old workaround for that (accessing the shares through ~/.gvfs or to symlinks to the mount points therein) is no longer accessible.

---

### Post by JohannB on 2010-11-24
@taiyal: This is not a feature and may even be a bug. This happens when gvfs-fuse-daemon is not started. I'm not quite sure why it did not start in your case, but you can try running the following from the command line:

```
/usr/lib/gvfs/gvfs-fuse-daemon ~/.gvfs
```

You should immediately see the mounted folders under ~/.gfvs

---

### Post by Monery on 2011-03-01
I just spent the past 2 hours looking for this answer to where Nautilus mounts the shares. When I discovered the folder, it seems to be locked and I can not write files to it. Why doesn't Nautilus put the share in a standard place like /media or /mnt

---

### Post by dmizer on 2011-03-01
> **Monery said:**
> Why doesn't Nautilus put the share in a standard place like /media or /mnt

Because creating folders and mount points in /media and /mnt requires root access. For what should be obvious reasons, running Nautilus as root to facilitate file sharing is extremely undesirable.

---

### Post by legendbb on 2012-11-22
Just to add on 10.10 it's mounted to ~/.gvfs

Command line to mount
```
$ sudo smbmount //{share_ip}/{directory} /mnt/SMBShared -o username=${user_name}/${DOMAIN_NAME}
```

Interesting part is, could not find a way to umount it without becoming root
I have "smbfs" & "cifs-utils" installed on the 10.10, but don't have smbumount command, "umount -l" & "umount -f" won't work as sudo.
After $ sudo su, I can do "umount -f" to umount the network share.

---

### Post by wildmanne39 on 2012-11-22
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

