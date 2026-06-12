---
title: "DVD-R not detected :("
date: 2007-08-14
forum: Multimedia &amp; Video
---

### Post by mebrahm on 2007-08-14
Hi,
I am a newbee to ubuntu. . I am having problem regarding the mounting of a dvd-r on my cd/dvd drive. I get the following error message

```

sudo mount /dev/hdc /media/cdrom0/
Password:
mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

``` :

my /etc/fstab is :
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sda8
UUID=c45b6a78-a0fc-4005-8d9e-a6d81d5366e3 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/sda1
UUID=049F-06A0 /media/sda1 vfat defaults,utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
# /dev/sda5
UUID=F80E-628D /media/sda5 vfat defaults,utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
# /dev/sda6
UUID=7083-4E0C /media/sda6 vfat defaults,utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
# /dev/sda7
UUID=1c5ac783-f36f-4571-a28a-427ab0925758 none swap sw 0 0
/dev/fd0 /media/floppy0 auto user,atime,noauto,rw,dev,exec,suid 0 0
/dev/hdc /media/cdrom0 auto users,noauto,atime,auto,rw,dev,exec,suid 0 0


```

could some one please help?

---

