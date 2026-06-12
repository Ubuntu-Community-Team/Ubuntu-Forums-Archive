---
title: "Can't mount NAS device"
date: 2009-12-18
forum: Networking &amp; Wireless
---

### Post by rbamforth on 2009-12-18
I'm trying to mount a Windows share to my Iomega NAS device. I've followed the instructions [here]("https://wiki.ubuntu.com/MountWindowsSharesPermanently").

When I execute "sudo mount -a" all is fine and I can access the drive in my /media/nas folder.

However when I shut down and restart the PC the drive isn't mounted automatically. It only gets mounted after I run "sudo mount -a" Any ideas anybody? 

Thanks.

- Roger

I'm running Jaunty and my fstab is

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda7
UUID=4a0608f9-b974-4cb4-90f0-c428e8f17315 /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/hda8
UUID=982779f3-a4e8-4f80-9afd-933cfb861087 /home           ext3    defaults,relatime        0       2
# /dev/hda1
UUID=BAD023E0D023A19D /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=0F6A05C45D7FCDA9 /media/hda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda6
UUID=3DA8171563132DE4 /media/hda6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb1
UUID=54906D24906D0DB4 /media/hdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda9
UUID=5a24c196-4c12-43b7-8813-1faa5864e050 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
:
/dev/sdb1            /media/external ntfs-3g    defaults,nls=utf8, 0      0
//192.168.1.40/nethdd  /media/nas      cifs       guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0


```

---

