---
title: "If the dvd drive is device /dev/hda/ is it a problem?"
date: 2008-01-10
forum: Multimedia &amp; Video
---

### Post by bwallum on 2008-01-10
Hi, I've removed my IDE hard drive, installed two SATA drives and re installed clean Ubuntu  7.10 AMD64.

All went well, even succeeded in restoring my home directory. I can stream BBC News ok and generally everthing is fine, except...

I can't play dvds now. It is the same drive that played dvds faultlessly before. The media appears as an icon on the desktop ok, correctly titled. Movie Player, MPlayer and VLC Player all see the dvd, spin it up and then futtttt. Never runs long enough to get anything on screen.

It is the only drive on my IDE cable and is set to master. The dvd drive shows as device /dev/hda. I have linked to dev/dvd. It mounts to directory media/cdrom.

Any ideas on how to get it playing?

Regards
Bob

---

### Post by Seti on 2008-01-10
yeah I think so because your SATA's should show up as /dev/sda and /dev/sdb. The DVD ROM that remains on IDE should now be /dev/hda.
Are your movie players set up to recognize /dev/hda as cdrom? what does your /etc/fstab look like?

---

### Post by bwallum on 2008-01-10
SATAs are /dev/sda1 and /dev/sdb1(this mounted as /media/disk). dvdrw drive is device /dev/hda mounted as /media/cdrom.

fstab is:-

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=f4adee08-311b-4cc5-99d3-a6b00e4624a6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=e2bc4c6c-c489-419f-90ca-36fb04df6396 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sdb1	/media/disk	ext3	defaults	0	0

EDIT
Can you believe it! I forgot the &%£$"!**css2 file! I must have BSE! Argggghhhhhh!!!!

---

