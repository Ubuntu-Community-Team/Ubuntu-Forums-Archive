---
title: "Samba and hidden folders"
date: 2009-11-29
forum: Networking &amp; Wireless
---

### Post by neon401 on 2009-11-29
Hi

I have recently installed Ubuntu Server 9.10 on an old computer I had lying around.
I've connected my external USB hard drive to it and managed to share it through samba, and all is fine.

Except when I browse through the hard drive in Windows, all the hidden files and folders are shown. I have attached a screen shot below.

How can I hide these?

Thanks for any help!

Also, here is my smb.conf
```

[global]
    ; General server settings
    netbios name = Media
    workgroup = Nalum
    security = user

[root]
    path = /
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = media

[WD1TB]
path = /mnt/wd
browseable = yes
read only = no
guest ok = yes
create mask = 0644
directory mask = 0755

```

---

