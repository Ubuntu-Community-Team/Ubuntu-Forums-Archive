---
title: "Windows PC doesn't see Samba share, but can connect manually"
date: 2010-08-29
forum: Networking &amp; Wireless
---

### Post by clockb0x on 2010-08-29
I'm running Lucid and and trying to get Samba set up to allow sharing files on my network.  My problem is that my Windows laptop (Win7) can't see the Linux PC when I click on Network.  It only shows my own laptop and my roommate's Vista laptop.  However, if I manually connect to the computer (\\serenity) it works just fine.

Right now I'm simply using the smb.conf that comes with the package and adding my share info.  The relevant section is:
```

[media]
   path = /media-zfs
   comment = Multimedia Storage
   browseable = yes
   read only = no
   public = yes
   hide unreadable = yes
   guest ok = yes

```

Any ideas on why it doesn't show up?  I've done a lot of searching online but haven't found anything that works.

---

### Post by headvampyre@hotmail.co.uk on 2010-08-29
try joining your laptop to the workgroup, thenaccessing it how you would with vista(i dont use win7 or vista so bear with me) hopefully that should help.

---

### Post by clockb0x on 2010-08-29
> **headvampyre@hotmail.co.uk said:**
> try joining your laptop to the workgroup, thenaccessing it how you would with vista(i dont use win7 or vista so bear with me) hopefully that should help.

Oh yeah, I forgot to mention, they are both already set to a workgroup of WORKGROUP.  Is there anything special to "join" a workgroup?

---

