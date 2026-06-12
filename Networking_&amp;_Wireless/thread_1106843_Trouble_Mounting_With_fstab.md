---
title: "Trouble Mounting With fstab"
date: 2009-03-26
forum: Networking &amp; Wireless
---

### Post by umechanism on 2009-03-26
When booting up Ubuntu, I get the following message:

```
CIFS VFS:  Cifs_mount failed w/return code = -6
```

The booting process stops and just waits.  Finally, if I hit CTRL-ALT-DEL the process continues but none of my remote shares get mounted.  I've recently posted about this but I thought I had it resolved due to another issues I found.  Guess not.:confused:

Here is my fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=c40e0e12-e7bf-44aa-a059-bb1495a9dcca /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=e4956b75-91e0-4691-92bd-3edfd412cd5b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       

#192.168.2.176:/shares/Volume1/FileShare /mnt/mediavault/FileShare smbfs defaults 0 0
#192.168.2.176:/shares/Volume1/Backup /mnt/mediavault/BackUp smbfs defaults 0 0
#192.168.2.176:/shares/Volume1/CinemaNow /mnt/mediavault/CinemaNow smbfs defaults 0 0
#192.168.2.176:/shares/Volume1/MediaShare /mnt/mediavault/MediaShare smbfs defaults 0 0

#Turn on VirtualBox USB access
#none /proc/bus/usb usbfs devgid=126,devmode=664 0 0

#oVolume 1 Mounting 320 Gig
//192.168.2.176/shares/Volume1/FileShare /mnt/hpmediavault/Volume1/FileShare cifs nounix,uid=michael,gid=michael,file_mode=0777,dir_mode=0777 0 0
//192.168.2.176/FileShare /mnt/hpmediavault/Volume1/FileShare cifs nounix,uid=michael,gid=michael,file_mode=0777,dir_mode=0777 0 0

//192.168.2.176/Backup /mnt/hpmediavault/Volume1/Backup cifs nounix,uid=michael,gid=michael,file_mode=0777,dir_mode=0777 0 0
//192.168.2.176/CinemaNow /mnt/hpmediavault/Volume1/CinemaNow cifs nounix,uid=michael,gid=michael,file_mode=0777,dir_mode=0777 0 0
//192.168.2.176/MediaShare /mnt/hpmediavault/Volume1/MediaShare cifs nounix,uid=michael,gid=michael,file_mode=0777,dir_mode=0777 0 0


#Volume 2 Mounting 1TB 
//192.168.2.176/Images /mnt/hpmediavault/Volume2/Images cifs nounix,uid=michael,gid=michael,file_mode=0777,dir_mode=0777 0 0

```
There are a lot of commented lines "#" because I've tried so many different mount methods.  The device listed is an HPMediaVault which is a network attached storage device.

I'd appreciate any help.

Mike

---

