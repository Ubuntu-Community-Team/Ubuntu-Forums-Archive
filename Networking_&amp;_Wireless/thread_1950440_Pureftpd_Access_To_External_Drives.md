---
title: "Pureftpd Access To External Drives"
date: 2012-03-31
forum: Networking &amp; Wireless
---

### Post by mildenhall on 2012-03-31
I have set up pureftpd on Ubuntu 12.04 and everything works fine on the local drive, but not for my external USB hard disk, /dev/sdb1, /media/GEP.

When I log in to pureftpd I'd just like to see my external USB drive, and nothing else. When I set up a link, or point pureftpd at the drive, I get told I do not have the correct permissions or "not allowed". Is there a way to do this please?

Unfortuately it's partition is FAT32. (I need FAT32 for when I pug it in to Windoze)

The USB hard disk is mounted and owned by my admin login. Nautilus will not let me change the owner or group to ftpuser or ftpgroup.

TIA

---

### Post by mildenhall on 2012-04-01
```
sudo mkdir /home/ftpusers/loginname/fakedrivename
sudo mount /dev/sdb1 /home/ftpusers/loginname/fakedrivename
```

This all works fine, BUT.........

How do I make this permanent?

---

### Post by Lars Noodén on 2012-04-01
You make it permanent by putting an entry for it in [/etc/fstab](http://manpages.ubuntu.com/manpages/oneiric/en/man5/fstab.5.html)  Compare the output from [mount](http://manpages.ubuntu.com/manpages/oneiric/en/man8/mount.8.html) with your current fstab and look at the manual page for fstab to get an idea of how the entry should look.  Be sure to make a backup copy of fstab before messing with it.

---

### Post by mildenhall on 2012-04-10
Yep, thanks, I finally worked it out...

```
/dev/sdb1 /media/GEP vfat umask=0000 0 0
/dev/sdb1 /home/ftpusers/jerry/GEP vfat umask=0000 0 0
```

---

