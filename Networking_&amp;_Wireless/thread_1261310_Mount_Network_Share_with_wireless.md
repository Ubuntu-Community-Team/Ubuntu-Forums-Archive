---
title: "Mount Network Share with wireless"
date: 2009-09-08
forum: Networking &amp; Wireless
---

### Post by stevezemlicka on 2009-09-08
I am having trouble mounting my network shares on boot.  I am using ubuntu 9.04 x64.

I followed this: [http://ubuntuforums.org/showthread.php?p=6651122](http://ubuntuforums.org/showthread.php?p=6651122) but all that got me was not having to type my keyring password or whatever that's called.

here is my fstab

proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=9083d9ff-bf3b-4cf7-8b63-7655cc06b195 /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=9022d5aa-580c-40c3-9e37-f5c846bc0bb3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
//192.168.1.254 /mnt/nas cifs username=username,password=password,users,rw 0 0

Any ideas, thoughts, comments are appreciated.

---

