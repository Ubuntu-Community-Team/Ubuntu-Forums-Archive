---
title: "Jaunty mounting Samba share at boot"
date: 2009-05-05
forum: Networking &amp; Wireless
---

### Post by kevinatkins on 2009-05-05
Hi,

I've got a small, but annoying, problem regarding mounting Samba (or NFS, for that matter) shares at startup.

This was working fine until Intrepid, when it broke, and it still won't work with Jaunty. I should note that this problem only afflicts my desktop box, which has been upgraded through various iterations of Ubuntu to the current 9.04 version; a fresh 'bare metal' install on my laptop works correctly.

Here's my fstab:

```
# /etc/fstab: static file system information
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=a4d57183-c577-4a34-bdbd-d84f9ed51216 /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/sdb5
UUID=8e503cb4-206c-4276-ac90-24f90f240cef none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
#//landisk/public/ /mnt/landisk/	smbfs credentials=/etc/samba/credentials,nounix,iocharset=utf8,file_mode=0777,dir_mode=0777,auto	0	0
#server2:/mnt/landisk	/mnt/landisk	nfs	rw,hard,intr,sync,auto	0	0
//server2/landisk	/mnt/landisk	smbfs 	defaults,credentials=/etc/samba/credentials	0	0

```

If anybody can shed any light on the issue, I'd be grateful. At the moment, I'm having to issue a 'sudo mount -a' command every time I want to mount the share (which contains all my music!) and it's getting a bit tedious.

Many thanks!

PS - I use network manager on both the desktop and laptop, the desktop connects via ethernet only, the laptop either via ethernet or wireless.

---

### Post by Iowan on 2009-05-05
**smbfs** has been deprecated in favor of **cifs**.  [Here]("http://ubuntuforums.org/showthread.php?t=288534") is a How-To for mounting **cifs** shares.

---

