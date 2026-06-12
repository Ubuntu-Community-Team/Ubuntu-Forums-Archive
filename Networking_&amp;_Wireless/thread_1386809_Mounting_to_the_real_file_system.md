---
title: "Mounting to the real file system"
date: 2010-01-21
forum: Networking &amp; Wireless
---

### Post by Jules1 on 2010-01-21
Hello,

I using Ubuntu 9.10 and can't seem to mount network drives to my real file system. I can mount them using *gvfs-mount*, e.g.

gvfs-mount smb://ceylon/awet

For most applications this is fine (I can access the files through the hidden .gvfs-directory), but inside of some applications I can't see the hidden files/directories.
For example, I'm using Jabref to access a shared database, but I can't save to it, because it's not possible to find the mounted directories in the Jabref GUI (it also doesn't save when I manually enter the path). So I would like to mount to a point in my real file system.

I'm new to Linux and don't quite understand how the networking works. I've seen several examples with the *mount* command, but none seem to work for me. I always get the following error message.

$ sudo mount -t smbfs //ceylon/awet /media/ceylon

mount: wrong fs type, bad option, bad superblock on //ceylon/awet,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


Thanks for any help,
Jules

---

### Post by suseendran.rengabashyam on 2010-01-21
Hi,

I guess that "smbfs" package has not been installed in your machine, install the "smbfs" package before you mount the samba share.

The following command will install the "smbfs" package

sudo apt-get install smbfs

Hope this helps.

---

### Post by Jules1 on 2010-01-21
Thanks a ton! That was the problem.

---

### Post by suseendran.rengabashyam on 2010-01-21
Hi,

Please mark the thread as solved so that it will be useful for others.

---

