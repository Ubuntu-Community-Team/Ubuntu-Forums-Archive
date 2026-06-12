---
title: "Can network mount save password?"
date: 2010-03-15
forum: Networking &amp; Wireless
---

### Post by scottyja on 2010-03-15
Hi all, I'm new here and relatively new to Linux.  I have a DNS-323 home NAS with media files that I'm using with my HTPC.  I have a separate Ubuntu install in another room that successfully mounts the network drive with the following:
[INDENT][I]sudo mount -t smbfs -o username=XXXXXX  //dns323/Media /mountpoint
[/I][/INDENT]The only problem is when I reboot, the mount is gone.  I've found the entry for the mount in /etc/mtab and copied that to /etc/fstab, but that doesn't seem to work.  Is there a way to safely store the password so I can access the mount after a reboot (similar to Window's mapped network drive)?  

Thanks!

---

### Post by suseendran.rengabashyam on 2010-03-15
Hi,

You can refer this thread for more details

[http://ubuntuforums.org/showthread.php?t=1409720](http://ubuntuforums.org/showthread.php?t=1409720)

Hope this helps.

---

### Post by scottyja on 2010-03-15
> **suseendran.rengabashyam said:**
> Hi,

You can refer this thread for more details

[http://ubuntuforums.org/showthread.php?t=1409720](http://ubuntuforums.org/showthread.php?t=1409720)

Hope this helps.

Very helpful... many thanks!

---

