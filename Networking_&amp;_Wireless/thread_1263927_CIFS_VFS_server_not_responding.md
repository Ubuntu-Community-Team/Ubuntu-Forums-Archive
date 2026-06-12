---
title: "CIFS VFS: server not responding"
date: 2009-09-11
forum: Networking &amp; Wireless
---

### Post by jh0n on 2009-09-11
Searched plenty, and only found references to this error on shutdown...

I'm using an MSI Wind nettop with a 9.1 server installation.  The goal is to copy various XP/2003 shares to this box, and then rsync this box offsite.  I have no problem mounting my windows shares thru fstab, but any copy/rsync operation gives me the following:

```
CIFS VFS: server not responding
CIFS VFS: No response to cmd 46 mid 2929
CIFS VFS: Send error in read = -11
....
Host is down
```

I'm able to cp small files <~1mb, but anything else causes this to crash.  Quick mount -a, and I'm up and going again.  Ethernet controller is RTL8111/8168B PCI Express Gigabit Ethernet controller (rev02).

Any ideas?

---

### Post by jh0n on 2009-09-14
bump - anyone?

---

### Post by redmk2 on 2009-09-14
> **jh0n said:**
> Searched plenty, and only found references to this error on shutdown...

I'm using an MSI Wind nettop with a 9.1 server installation.  The goal is to copy various XP/2003 shares to this box, and then rsync this box offsite.  I have no problem mounting my windows shares thru fstab, but any copy/rsync operation gives me the following:

```
CIFS VFS: server not responding
CIFS VFS: No response to cmd 46 mid 2929
CIFS VFS: Send error in read = -11
....
Host is down
```

I'm able to cp small files <~1mb, but anything else causes this to crash.  Quick mount -a, and I'm up and going again.  Ethernet controller is RTL8111/8168B PCI Express Gigabit Ethernet controller (rev02).

Any ideas?

It would help to know what your fstab file looks like. Have you have installed the smbfs (CIFS) components.  

What do the logs show?  I'm assuming that the errors you have described are STDOUT terminal display.

Are you able to move large files under other conditions?

---

### Post by ubradford on 2009-12-06
I found a a fix for this issue.  It works on Karmic while using wireless. I posted it here:
[http://ubuntuforums.org/showthread.php?t=1347340](http://ubuntuforums.org/showthread.php?t=1347340)

---

