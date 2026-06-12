---
title: "cifs tries to mount before lan is up"
date: 2006-02-15
forum: Networking &amp; Wireless
---

### Post by tkay on 2006-02-15
Hello everyone, a total beginner here with a first post and a question...

I have a laptop with Breezy and a pc with xp and a shared folder.

I have written a line to fstab to automount the share in startup, but it does not work and here's the reason found in dmesg:

CIFS VFS: cifs_mount failed w/return code = -101

The error code 101 means that cifs attempts to mount network shares before networking is up and therefore of course fails. The question is: How can i fix this?
Any help would be greatly appreciated, thanks!

---

### Post by tkay on 2006-02-16
Any ideas?

---

### Post by ashrack on 2006-02-20
Try this when U boot to desktop and U have network connectivity:
```
mount -t cifs //network/share /media/networkshare
```

If this works then your NETWORKING is set to execute later than FSTAB which is wrong offcourse.Which I can try to help U out

---

