---
title: "mounting samba volumes using cifs"
date: 2010-10-22
forum: Networking &amp; Wireless
---

### Post by gmermoud on 2010-10-22
Hello people,

When trying to mount samba volume on my Ubuntu 10.04 distro, I get the following message:

```
mount: wrong fs type, bad option, bad superblock on XXX,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

The server XXX is however working fine (and I didn't make a mistake in /etc/fstab). Here is the output of dmesg | tail:

```

[842513.298334]  CIFS VFS: cifs_mount failed w/return code = -22
[842513.521658] VFS: busy inodes on changed media or resized disk sr0
[842513.523285] VFS: busy inodes on changed media or resized disk sr0
[842514.522865] VFS: busy inodes on changed media or resized disk sr0

```

and my fstab entry:

```

//xxx.yyy.ch/zzzz /mnt/kdrive cifs rw,user,noauto,username=myusername,workgroup=myworkgroup,uid=mylocalusername,gid=mygid,dir_mode=0700,file_mode=0600

```

Thanks for helping me on this one...

Greg

---

