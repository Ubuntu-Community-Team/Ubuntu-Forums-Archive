---
title: "Unable to mount a network drive on Ubuntu 10.04"
date: 2010-11-09
forum: Networking &amp; Wireless
---

### Post by suryaemlinux on 2010-11-09
Hi,
I'm unable to mount a network drive on my ubuntu 10.04. Here is how my  fstab looks like:

[B][I]
# Use 'blkid -o value -s UUID' to print the universally unique  identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>   <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=d9508c3b-fa02-4118-bafb-7cc0863af984 /               ext4     errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e8198847-f054-4721-a463-fd3c4efd236d none            swap    sw               0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0        0
192.168.1.38:/abc    /abc    nfs auto 0 0
192.168.1.38:/xyz    /xyz    nfs auto 0 0[/I][/B]


Both the network and local directories exist. 


This is what I did after boot-up:

[B][I]mount -t nfs 192.168.1.38:/abc /abc
mount: wrong fs type, bad option, bad superblock on 192.168.1.38:/abc,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
[/I][/B]


The above fstab configuration works for me flawlessly on my fedora. I  dunno what's the issue here. I don't see any error in the dmesg either.

---

### Post by blackmail on 2010-11-09
from the line where you mount your drive, drop everything after nfs, including nfs, mainly it should look like this:
```
//[computer_name]/[drive_name] /media/[mount_folder] smbfs guest 0 0
```
in your case SERVER is the IP

also instead of IP try to use the computer name. also did you install smbfs?
```
sudo apt-get install smbfs
```

and did you make a folder in media?
```
mkdir /media/[folder_name]
```

also to reload the fstab file type in:
```
sudo mount -a
```

for more info please see:
```
man mount.smbfs
```

Hope this helps

---

### Post by luvshines on 2010-11-09
> **suryaemlinux said:**
> Hi,
I'm unable to mount a network drive on my ubuntu 10.04. Here is how my  fstab looks like:

[B][I]
# Use 'blkid -o value -s UUID' to print the universally unique  identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>   <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=d9508c3b-fa02-4118-bafb-7cc0863af984 /               ext4     errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e8198847-f054-4721-a463-fd3c4efd236d none            swap    sw               0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0        0
192.168.1.38:/abc    /abc    nfs auto 0 0
192.168.1.38:/xyz    /xyz    nfs auto 0 0[/I][/B]


Both the network and local directories exist. 


This is what I did after boot-up:

[B][I]mount -t nfs 192.168.1.38:/abc /abc
mount: wrong fs type, bad option, bad superblock on 192.168.1.38:/abc,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
[/I][/B]


The above fstab configuration works for me flawlessly on my fedora. I  dunno what's the issue here. I don't see any error in the dmesg either.

Looks like you are trying to mount an nfs share.
Do you have mount.nfs executible in /sbin ?

Actually I mean, nfs-common package installed

---

