---
title: "not sure what Iam doing wrong"
date: 2007-11-07
forum: Mythbuntu
---

### Post by govee on 2007-11-07
I thought I had my Sda mounted to /var/lib/mythtv/recordings a couple weeks ago. I have been away and returned recently and now after restarting the machine it is not mounted. I can mount it through a terminal but not auto mount. Below is my fstab. I checked permissions for it after I mounted it and all permissions and ownership belong to MythTv.

 /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=2260e672-c190-41e0-8278-74cbe1b73c2a /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=454f45aa-c606-4340-8f38-d06d5df5353f none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sda1       /var/lib/mythtv/recordings auto RW 0 2

Just noticed I used caps for "RW" on that line. Could that cause a problem. I seem to remeber reading Linux is particular about caps usage.

---

### Post by Tekno_Cowboy on 2007-11-07
It's probably best to change the RW to rw first and see what happens after a reboot. If that doesn't work, try setting it up using the UUID method instead. I seem to have fewer problems that way, since the UUID is the same, except if you change the filesystem type.

---

### Post by superm1 on 2007-11-08
I agree.  The easiest way to get the UUID is by looking in /dev/disk/by-uuid

```
ls -l /dev/disk/by-uuid
```

---

