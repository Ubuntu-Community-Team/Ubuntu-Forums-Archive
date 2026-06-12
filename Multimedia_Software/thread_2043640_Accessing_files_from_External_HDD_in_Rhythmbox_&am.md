---
title: "Accessing files from External HDD in Rhythmbox &amp; Mediatomb"
date: 2012-08-17
forum: Multimedia Software
---

### Post by dabailey1971 on 2012-08-17
I'm an impressed Ubuntu Newbie but am having a bit of trouble with getting the most out of Rhythmbox & struggling to get Mediatomb to do anything at all...

1) Rhythmbox sees the music collection on my external USB HDD and can play it but it does not synch the music with my Android phone.  Podcasts however synch automatically with no issues.

2) I want to stream the same music to an LG Bluray player that is also a DLNA client but Mediatomb tells me that permission is denied so I can't even view the files in Mediatomb.  I tried 
david@david-HP-Compaq-2510p-Notebook-PC:~$ chmod ugo+rwx FREECOM HDD
chmod: cannot access `FREECOM': No such file or directory
chmod: cannot access `HDD': No such file or directory
david@david-HP-Compaq-2510p-Notebook-PC:~$ sudo chmod ugo+rwx FREECOM HDD
[sudo] password for david: 
chmod: cannot access `FREECOM': No such file or directory
chmod: cannot access `HDD': No such file or directory

It seems I'm doing something basic and incredibly stupid but I can't work out what - anyone got any ideas?

---

### Post by nothingspecial on 2012-08-17
You need to specify the full path and escape any spaces. You external drive is probably mounted at /media so the path would be ```
/media/FREECOM\ HDD
``` (notice the \ which deals with the space)

If your external drive is not using a linux file system, changing the permissions will not help.

---

### Post by dabailey1971 on 2012-08-17
OK Excellent - thanks for the \ tip.  I guess through this means that I need to get a new HDD and put a Linux filesystem on it and then copy over the contents?  or is there a way to access a FAT drive?

---

### Post by nothingspecial on 2012-08-17
Well, if you plan on using the drive exclusively with linux then copying the stuff to an ext4 formatted drive would be preferable. Of course, if the stuff is important to you, you should have a back up anyway.

You can set the permissions on a vfat drive when it is mounted using fstab. Set the ownership with uid and gid, and the permissions with umask, fmask an dmask

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

of course, once you have done that you may find that permissions are not the problem.

---

### Post by dabailey1971 on 2012-08-17
So I ended up with an fstab file that looks like this.  The drive is now mounted but permisson is still denied from Mediatomb.  I am guessing it is because of the 
users,uid=1000,gid=100, part of the entry - but can't find out what the right entries here would be.

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=2d08be1c-00e4-4cf5-b7a7-b8ddc3cd8522 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
#UUID=bf800a28-1e6a-4932-9e56-a686ebe0fd24 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
# FAT ~ Linux calls FAT file systems vfat)
# /dev/hda1
UUID=11ED-3324  /media/windows  vfat auto,users,uid=1000,gid=100,dmask=000,fmask=111,utf8  0  0

---

### Post by dabailey1971 on 2012-08-18
Not entirely sure what happened.  Perhaps just needed a reboot but everything is working perfectly this morning!  Thanks very much indeed for your support!

---

