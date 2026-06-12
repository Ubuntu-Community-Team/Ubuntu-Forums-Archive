---
title: "NFS share won't auto mount"
date: 2009-01-16
forum: Networking &amp; Wireless
---

### Post by plasmafusion on 2009-01-16
hey all...
accessing my file server using nfs (through an entry in fstab).
on boot the share's not mounted. i need to use mount -a and then it's fine.
any ideas?
my fstab entry looks something like this...
```
10.0.0.16:/share /media/share nfs rsize=8192,wsize=8192,timeo=14,intr
```

---

### Post by PaganBlasphemy on 2009-01-23
I'm having the same problem with a brand new 8.10 installation.  I'm trying this at the moment, will update this post if it is sucessful:

[http://ubuntuforums.org/showthread.php?t=1048074&highlight=%2Fetc%2Ffstab+automatically+mount](http://ubuntuforums.org/showthread.php?t=1048074&highlight=%2Fetc%2Ffstab+automatically+mount)

Basically, setting the mounting in /etc/fstab to not automount, and then once everything is loaded up, /etc/rc.local will do the mounting.  At least as far as I can understand, that is what is happening.

What version is Ubuntu on, and handling networked shares is STILL a PITA?  Heh...;)

---

### Post by plasmafusion on 2009-01-23
that worked a treat :)
didn't come across that thread in my searches.
cheers mate.

---

