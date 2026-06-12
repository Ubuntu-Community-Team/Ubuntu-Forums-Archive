---
title: "can't play dvd/ cds due to error: &quot;mount: special device  /dev/scd0 does not exist&quot;"
date: 2010-05-24
forum: Multimedia Software
---

### Post by frederikbjerreandersen on 2010-05-24
my wife's ubuntu-driven laptop can't play any dvd's or cd's. 

When you insert a disc, the small green light flashes and the discdrive seems to be running/reading the device for appr- 10 seconds. But nothing happens - if you try to open/ play it manually, this message pops up:

"Cannot mount cdrom0 /mount: special unit /dev/scd0 does not exist" (in  danish, though)

The cdrom0 unit is shown in the computer-directory but is still not  recognized. I've trid to find a solution through Google, but got no helpful answer  yet. 

The etc/fstab-file looks like this:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=28a4a919-1061-4a5d-9aee-d4e58a0ab3ba /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=1fec4565-3f47-4cea-b961-7af14c396160 none            swap    sw              0       0
/dev/scd0 /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

anyone?

---

### Post by ajgreeny on 2010-05-24
Interestingly, having just looked, my fstab does not contain any entry at all for the cdrom drive, and my system works as it should.

Following on from that, try commenting out the cdrom line in yours and try again, after a restart, perhaps, or at least after a ```
sudo mount -a
```

---

