---
title: "Active Directory Samba Share Permission Problem"
date: 2011-02-24
forum: Networking &amp; Wireless
---

### Post by nmushov on 2011-02-24
Hi everyone. I'm having a problem with Active Directory and Share permissions that I cant seem to figure out.

I used likewise-open to join my ubuntu server to a windows 2008 domain. Everything seems to be working fine. The problem is, the only way I can access the shares is if I CHMOD 777 the share directory. If I CHMOD 770, the Domain owner or Domain group member of the directory cant access the directory. Also, when creating a folder within the share, I need to set the directory mask as 777 in order to enter those sub folders. 

Heres the share section from my smb.conf
```
[public]
    comment = Ubuntu File Server Share
    path = /srv/samba/public
    browseable = yes
    read only = no
    create mask = 777
    directory mask = 777
    valid users = @"NCC\Domain Users"
```

Thanks in advance for any help.

---

### Post by nmushov on 2011-02-25
Ok, solved this by purging likewise open, samba, and winbind and re-installing. Gremlins.

---

