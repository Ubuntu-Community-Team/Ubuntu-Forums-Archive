---
title: "fstab"
date: 2008-11-03
forum: Multimedia Software
---

### Post by jerlinux on 2008-11-03
I should not have been messing with my fstab. Since I have messed with it, none of my dvd drives will mount. Gives me the next line can't have a g or some such thing.

I hoped that upgrading to 8.1 would bring in a new fstab but it did not. 

I will attach a copy of the current fstab. Can anybody tell me what I can change to get the dvds back? Does 8.1 even use fstab or does it find some other way to mount the drives?


Note previously posted in absolute beginner section.

---

### Post by sisco311 on 2008-11-03
post the output of:
```
lshw -C disk
```

---

### Post by puppywhacker on 2008-11-03
my DVD writer entry in my fstab looks like this
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

So it's pretty much the same. what happens when you do manual mount with a DVD or CD in the player? does it even spinup?
mount /media/cdrom0

What are the last 20 lines in your messages-log?
tail -20 /var/log/messages

somehow I always have the feeling that the nautilus file browser is nowadays the way ubuntu should automount the disks as soon as they are entered, but I never figured out how it works. For me as soon as I enter a disk I go to nautilus and click the disk from the lefthand panel. That also triggers an icon on my desktop, it is then also mounted on /media/cdrom0

goodluck

---

### Post by jerlinux on 2008-11-03
Put one in word just in case.

---

### Post by sisco311 on 2008-11-03
edit the fstab to:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=cec9f218-bc0e-4a7d-8c99-21aa2ac433c4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=8caa6a2a-8d03-46ac-ab8a-6b81c02a0da4 none            swap    sw              0       0
[B]/dev/scd0        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8     0       0
/dev/scd1        /media/cdrom1   udf,iso9660 user,noauto,exec,utf8[/B]     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by jerlinux on 2008-11-03
puppywhacker:

I don't know if the fstab will mount your cdrom, when I made mine look like yours, the cd came right back alive.

sisco311:

I cut and pasted the suggested change into my fstab and rebooted.  The cdrom is alive.  I did not try the floppy but it is very rarely used anyway and should probably be removed.

Thanks to both of you for helping out a newbe.  I will not be messing with the fstab again anytime soon and even if I am tempted to screw around, I will make a back up copy before I gedit anything again.

Thanks again.

---

