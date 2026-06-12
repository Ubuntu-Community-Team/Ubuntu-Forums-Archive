---
title: "CIFS auto-unmount on shutdown / reboot"
date: 2012-04-03
forum: Networking &amp; Wireless
---

### Post by skobiyan on 2012-04-03
Hi!

I am currently using Kubuntu 12.04 and my laptop (which mounts 2 CIFS drives, as shown below) will not shutdown or reboot unless I manually umount the CIFS drives. I would like to automate this process, but have no idea how.

I have, of course, Googled this issue and tried various solutions, but to no avail.

Surely someone out there is successfully doing this, and I would like to know how it can be done.

Thank you!

```

//10.0.0.50/archive     /mnt/archive    cifs            users,auto,credentials=/etc/samba/credentials,noperm 0 0
//10.0.0.50/backup      /mnt/backup     cifs            users,auto,credentials=/etc/samba/credentials,noperm 0 0

```

---

### Post by papibe on 2012-04-04
Hi skobiyan. Welcome to the forums!

Take a look at the troubleshooting section of this howto: [Mount samba shares with utf8 encoding using cifs]("http://ubuntuforums.org/showthread.php?t=288534")

Regards.

---

### Post by skobiyan on 2012-04-18
Papibe,

Thank you very much for your reply. I did follow that link, and (as the intertubes often do) through hyperlink after hyperlink I was led to the solution I sought for.

In short, in (k?)network-manager (or whatever the kubuntu GUI is for managing networks) has an option for Wireless networks labelled 'System Connection'. By default, this is unchecked. Enabling this option has since allowed my laptop to shutdown / reboot very quickly, as desired.

I sincerely hope this helps others flummoxed by slow/never-ending reboots/shutdowns.

Thanks again!
Sk

---

