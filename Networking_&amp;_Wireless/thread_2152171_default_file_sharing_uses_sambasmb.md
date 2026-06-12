---
title: "default file sharing uses samba/smb?"
date: 2013-06-07
forum: Networking &amp; Wireless
---

### Post by cheeseburger38 on 2013-06-07
Does the file sharing option available by right clicking on a folder/file in the file explorer use Samba underneath?

---

### Post by deadflowr on 2013-06-07
Yes
When you attempt to share by right clicking and enabling sharing, it'll ask to install samba and other smb related packages.

---

### Post by Morbius1 on 2013-06-07
It uses a different type of samba share though called a Usershare. If you try to find the share definition in /etc/samba/smb.conf you aren't going to find it. The share definitions are in /var/lib/samba/usershares.

To get a list of all the shares created through Nauitlus and how they are configured you can run this command:
```
net usershare info --long
```

---

