---
title: "Large files fail to copy to smb share!"
date: 2012-10-29
forum: Networking &amp; Wireless
---

### Post by n1ght28 on 2012-10-29
While accessing the smb share hosted on my raspberry pi (a mounted usb hard drive)
from a ubuntu laptop via wifi I encounter two problem

1) get a disk full error when trying to copy files over to the share from the laptop,
2) if I hit "copy anyway" and the file is over 100mb aprox, it fails after a few mb.

the smb share is mounted on the laptop using fstab

here is my fstab
```
/dev/sda3       /               ext4    errors=remount-ro 0       1
//192.168.1.18/public /media/pi cifs uid=myuser,credentials=/home/myuser/.smbcredentials,iocharset=utf8,file_mode=0777,dir$
# swap was on /dev/sda5 during installation
UUID=60df05e9-f81c-493c-a338-f6fa33b2d9f5 none            swap    sw              0       0
```

my /etc/samba/smb.conf
```
[public]
  comment = Public Storage
  path = /home/shares/public
  admin users = root
  available = yes
  read only = no
  browsable = yes
  public = yes
  writeable = yes
```

any ideas where I'm going wrong?

---

