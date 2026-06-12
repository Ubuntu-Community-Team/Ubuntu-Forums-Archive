---
title: "Can't play DVD's or recognize them."
date: 2012-08-31
forum: Multimedia Software
---

### Post by j1mp492 on 2012-08-31
Can't play DVD's or even recognize them, but CD's works fine. I've tried serveral things but nothing seems to work, also I got "restricted extras", "medibuntu", "libdvd" and all that installed.

"sudo lshw -C disk" output
```

  *-cdrom
       description: DVD-RAM writer
       product: DVDRAM GT51N
       vendor: HL-DT-ST
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr0
       version: AS00
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc
```

/etc/fstab/

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=2d86d777-e673-4a3e-ab23-3d1b8b2de432 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=6b9c061e-d6b9-41be-910a-9252151e1d79 none            swap    sw              0       0
```

/etc/mtab/

```
/dev/sda1 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
gvfs-fuse-daemon /home/karin/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=karin 0 0
gvfs-fuse-daemon /root/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev 0 0
```

"dmesg | grep -i dvd" output

```
[    2.259608] ata2.00: ATAPI: HL-DT-ST DVDRAM GT51N, AS00, max UDMA/133
[    2.267549] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GT51N     AS00 PQ: 0 ANSI: 5
[    2.274495] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray

```

That's what I got so far, hope someone is able to get something out of it. Thanks!

---

### Post by Rodney9 on 2012-09-01
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by j1mp492 on 2012-09-01
> **Rodney9 said:**
> [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)
Thanks, but I have a question.. Why are you linking an article that tells me to install libdvdread4?
> also I got "restricted extras", "medibuntu", "libdvd" and all that installed.

---

### Post by j1mp492 on 2012-09-02
> **jsbill said:**
> Check the format of it then i can help you. I did not recognize it also

The format of what?

---

