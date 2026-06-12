---
title: "Mount a Windows share in the server."
date: 2005-12-18
forum: Networking &amp; Wireless
---

### Post by xeo_pt on 2005-12-18
Hi,
I need to mount in the server a windows share for backup pourpouse.
I try [COLOR="Lime"]mount -t smbfs //windowsmachine/folder /mnt/windows[/COLOR]
but it doesn't work.

If some one can help.
Thanks in advance.

---

### Post by Koybe on 2005-12-18
If it's a win2003 server you should use :
```
mount -t cifs //windowsmachine/folder /mnt/windows
```

Be sure to have smbfs package installed too. ;-)

---

### Post by mlomker on 2005-12-18
Might want to take a look at [this thread.]("http://ubuntuforums.org/showthread.php?t=102728")

---

### Post by xeo_pt on 2005-12-18
That's it!
My mistake was in the share, I share the drive and it as to be shared a folder.

Thanks to all of you.

---

