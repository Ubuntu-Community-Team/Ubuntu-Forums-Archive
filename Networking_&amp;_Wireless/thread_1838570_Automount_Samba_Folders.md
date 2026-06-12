---
title: "Automount Samba Folders"
date: 2011-09-03
forum: Networking &amp; Wireless
---

### Post by tokyo-joe on 2011-09-03
How can I automount samba folders shared in my home network at boot? I am assuming it's just a matter of syntax.

What I have tried so far (but without success) are (in /etc/fstab):
```

//multimedia/raid1 /media/raid smbfs username=foobar,passsword=foobar,defaults 0 0

//multimedia/media/raid1 /media/raid smbfs username=foobar,passsword=foobar,defaults 0 0

//192.168.1.102/raid1 /media/raid smbfs username=foobar,passsword=foobar,defaults 0 0

//192.168.1.102/media/raid1 /media/raid smbfs username=foobar,passsword=foobar,defaults 0 0

```

Notes:
-"multimedia" is the NetBIOS name of the samba server machine.
-"192.168.1.102" is the IP address of the samba server machine.
-"/media/raid1" is the exact directory on the samba server machine.
-"raid1" is the samba share name of the shared folder.

---

### Post by Toz on 2011-09-03
smbfs is deprecated. Use cifs instead. See: [https://wiki.ubuntu.com/MountWindowsSharesPermanently]("https://wiki.ubuntu.com/MountWindowsSharesPermanently")

---

### Post by tokyo-joe on 2011-09-04
Thanks, it works on my Natty.

---

