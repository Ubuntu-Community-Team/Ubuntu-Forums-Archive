---
title: "Slow to open network shares"
date: 2009-11-12
forum: Networking &amp; Wireless
---

### Post by KlytusLord on 2009-11-12
Hello everyone,

My network consists of 10 computers, 7 running Windows 7 (just coincidence), 1 running Windows Server 2008 R2, and two running Ubuntu 9.10.

I am a Linux newbie, and I am wondering if the following is normal.

From either Linux machine (one is a desktop, wired, and the other is a laptop, wireless) when I access the network, finding and opening the shares from other machines is very slow.  This is only in the opening process; once the share is opened, file operations are normal speed.

This does not happen on any of the Windows machines, and accessing the Linux shares from a Windows machine is also not a problem at all.

The slow opening even happens when the Linux laptop accesses the Linux desktop, so it's not just with the Windows shares.

So, is this normal or is there some setting to improve the browsing of shared folders across the network?

Thanks for any information that may help.

---

### Post by simeonuk on 2009-11-13
Hi

I'm also having similar issues.  I have files hosted on a Vista machine that are really slow to access from 9.10 but it's the whole process, ie, media files are extremely slow to stream.


Any help would be greatly appreciated!

Si

---

### Post by moloth on 2009-11-26
Try this:

$sudo apt-get install smbfs winbind
$sudo gedit /etc/nsswitch.conf

Add wins to this line before dns:

hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4

$sudo reboot

---

### Post by midgemiles on 2009-12-13
Thanks for that tip.  I had the same problem and it is now fixed following your instructions.  I don't know how we'd get on without the forum.:D

---

### Post by kitno84 on 2009-12-31
> **midgemiles said:**
> Thanks for that tip.  I had the same problem and it is now fixed following your instructions.  I don't know how we'd get on without the forum.:D
hear, hear.

helped me too.

---

