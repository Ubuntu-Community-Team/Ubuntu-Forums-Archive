---
title: "mount on boot partition 1 in pc A (partition 1 is in pc B)"
date: 2010-09-26
forum: Networking &amp; Wireless
---

### Post by t0ze on 2010-09-26
Hey ppl,

I have a desktop with samba share (is running on ubuntu 9.10) ii have shared 3 partitions of the same HD
/ubuntu/partition1
/ubuntu/partition2
/ubuntu/partition3
(this is configured in samba on PcB)

Now, in this pcA i can see that partitions, but i don't know what to do so i can mount parition1 on boot. i've edited /etc/fstab like this

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
/dev/sda5    /    ext4    errors=remount-ro    0    1
/dev/sda1    /media/Recovery    ntfs    defaults,nls=utf8,umask=0222    0    0
/dev/sda2    /media/System_Reserved    ntfs    defaults,nls=utf8,umask=0222    0    0
/dev/sda3    /media/sda3    ntfs    defaults,nls=utf8,umask=0222    0    0
/dev/sda6    none    swap    sw    0    0
smb://ubuntu/art/    /mnt/samba     smbfs     username=xxx,password=xxxxxx 0 0

any help ?
Tks in advance.

---

### Post by luvshines on 2010-09-26
Didn't get your question :confused:

Having trouble with mounting CIFS share via fstab ??

See if this helps, comment #7 from following
[http://ubuntuforums.org/showthread.php?t=1576979](http://ubuntuforums.org/showthread.php?t=1576979)

You know how to mount the share through command line ?

---

### Post by t0ze on 2010-09-27
it helped.

Tks luvshines

---

