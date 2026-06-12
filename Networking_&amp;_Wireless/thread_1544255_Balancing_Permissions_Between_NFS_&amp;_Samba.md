---
title: "Balancing Permissions Between NFS &amp; Samba"
date: 2010-08-02
forum: Networking &amp; Wireless
---

### Post by tracyandskye on 2010-08-02
If we save a file through NFS it opens as read only in Samba.  I'm assuming I just don't have my permissions set right but I can't figure it out.

Here's my Samba file:

```
[global]
workgroup = voodoonet
netbios name = Curley
name resolve order = bcast host lmhosts wins

map to guest = Bad User
local master = yes
preferred master = yes
os level = 65
usershare allow guests = Yes
usershare max shares = 100
usershare owner only = False

wins support = no

[Curley Data]
path = /media/Data
available = yes
browsable = yes
public = yes
writable = yes

```

and my exports file:

```
/media/Data/server/Business/BPS 192.168.0.1/24(rw,no_root_squash,async)
```

---

