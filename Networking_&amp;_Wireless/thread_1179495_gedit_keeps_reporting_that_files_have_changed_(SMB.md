---
title: "gedit keeps reporting that files have changed (SMB fstab mount)"
date: 2009-06-05
forum: Networking &amp; Wireless
---

### Post by mattalexx on 2009-06-05
I am auto mounting a Samba share from my Gutsy file server in the other room. Everything is working perfectly except for one thing: If I use Gedit to edit files on the share, it keeps reporting that the file has changed (see attached PNG). It seems to happen randomly -- I can't seem to recreate it reliably. Anyway, here is my fstab entry:
```

//192.168.0.3/matt /mnt/mattserver smbfs auto,user,exec,rw,async,uid=matt,username=matt,password=[PASSWORD] 0 0

```

EDIT: I should mention that there are weird backup files being saved in the directory ("cifsd6c9", "cifsd58a", ...) even though I have unset the "Create a backup copy of files before saving" option in Gedit.

---

