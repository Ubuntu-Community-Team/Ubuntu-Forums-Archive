---
title: "DVDs won't play"
date: 2005-10-29
forum: Multimedia &amp; Video
---

### Post by adamthompson on 2005-10-29
I can't get DVDs to play. In Totem, I get the error message "Failed to find mountpoint for device /dev/hdc in /etc/fstab". I've also tried MPlayer and Ogle, which won't work either.

Any ideas?

---

### Post by aysiu on 2005-10-30
Apparently, someone else is experiencing this, too, in Red Hat:
[https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=170068](https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=170068)

It must be a Gnome thing, but I'm running Gnome and haven't encountered that problem. Hm. Well, I guess you can file the Bug with Ubuntu as well (see the top-right link).

---

### Post by adamthompson on 2005-10-30
Thanks. I'm not sure my problem is exactly the same as the Red Hat bug. CDs (audio or data) mount fine. But I can't mount DVDs (video or data).

Here's my /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0


Does that look OK?

---

