---
title: "Mounting SMB Shares from Server with netbios aliases"
date: 2009-04-06
forum: Networking &amp; Wireless
---

### Post by mosestruong on 2009-04-06
There is a Samba server which has different shares depending on what NET BIOS name was used to connect to it.

I'm able to mount any of the shares using the default NET BIOS name, however I can't do that when trying it for shares associated with its aliases.

I've tried using 
```
sudo mount -t cifs //alias/share /mnt -o ip=xx.xx.xx.xx,domain=WORKGROUP,credentials=/root/credentials

```

But I get the following error:

```
mount error 6 = No such device or address
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

```

I've tried specifying servern=alias as well, but it still gives the same error message. Anyone has a solution to this?

---

