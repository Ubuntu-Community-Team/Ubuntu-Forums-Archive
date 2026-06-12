---
title: "CIFS ERROR: mount error 13 = Permission denied"
date: 2009-03-10
forum: Networking &amp; Wireless
---

### Post by Kismet on 2009-03-10
I know this has been asked before, but I cannot find a solution that works for me.

```
sudo mount -t smbfs //10.10.10.36/NetUsers /home/lbox/mail -o user=administrator
```

Works

```
smbmount //10.10.10.36/NetUsers /home/lbox/mail -o username=administrator
```

Works

```
fstab:
//10.10.10.36/NetUsers /home/lbox/mail smbfs user=adminstrator 0 0
```

DOES NOT WORK WTF?

```
lbox@lbox-desktop:~$ sudo mount -a
Password: 
mount error 13 = Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
lbox@lbox-desktop:~$
```

Any help or suggestions??? I'm at my wits end here.

Thanks alot.

---

