---
title: "Problems with samba mounting via fstab"
date: 2010-04-15
forum: Networking &amp; Wireless
---

### Post by Xi0N on 2010-04-15
Here is the thing:

I have a server, call it remoteserver (windows machine).
This machine has two samba shares
share1 and share2

i edited /etc/fstab to mount both at boot time with the info on fstab:


```
//remoteserver/share1 /media/remoteserver-share1 cifs credentials=/etc/samba/remoteserver-user   0   0
//remoteserver/share2 /media/remoteserver-share2 cifs credentials=/etc/samba/remoteserver-user   0   0

```

So, after i reboot, the system will only mount the last samba mount defined line on fstab, in this case, only remoteserver-share2 would be mounted.
If i change the lines order, it will be remoteserver-share1 the one mounted.

Why does this happen?

---

