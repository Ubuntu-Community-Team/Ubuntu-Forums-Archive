---
title: "cd drive recognized but not"
date: 2010-02-16
forum: Multimedia Software
---

### Post by baboo on 2010-02-16
I am using 9.10. If I put in a audio cd an icon appears on desktop but nothing shows in /media/cdrom0. I can click on icon an open with rythmbox and play cd. Same thing applies with dvd movies. Icon appears on Desktop and I can watch with movieplayer.

However, nothing shows in /media/cdrom0. If I open the file browser, I see that the cd drive is mounted but it will not display contents. I get the error message 'Dbus error'. 

also, Handbrake and winff cannot find drive.

here is my fstab:
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=50073f9c-cb66-4ba5-adfa-d45fd73064ac /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=cac47415-29d5-44f8-927d-1fd5d798c483 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


here is df -h output:
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             106G  9.7G   91G  10% /
udev                  975M  240K  975M   1% /dev
none                  975M  408K  975M   1% /dev/shm
none                  975M  196K  975M   1% /var/run
none                  975M     0  975M   0% /var/lock
none                  975M     0  975M   0% /lib/init/rw

as you can see, its not showing cd drive mounted.

Previous Ubuntu versions worked but 9.10 isn't. I've tried other distros and they work fine. I want to use Ubuntu so I am hoping someone can help.

thanks

---

### Post by quixote on 2010-02-17
A strange situation.  You mention that it does this with audio CDs.  Does it also do it with data CDs or Ubuntu LiveCDs?  What do the following commands tell you after you've put a CD in the drive?```
sudo fdisk -l       *("l" as in list)*
```Assuming that returns a line with something cd-like in it, what happens if you use that exact device name in a manual mount command?  Eg, let's say fdisk told you the cd was /dev/scd0. ```
sudo mount /dev/scd0 /media/cdrom
```

---

