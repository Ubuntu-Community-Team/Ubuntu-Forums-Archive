---
title: "SAMBA problem - files inaccessable"
date: 2011-05-10
forum: Networking &amp; Wireless
---

### Post by wgregori on 2011-05-10
I'm a SAMBA newbie... got it up and running and can see my drives on my Windows network but only one will allow me to manipulate the files.  I have two drives defined in samba.conf but only the [gregorigroup] allows full access. [big_part] allows me to see the files but I can not copy to and from drive.
Any help would be much appreciated.  Thanks

[big_part]   <-- Does NOT allow me to manipulate files
  comment = Unused Partition
  path = /big_part
  valid users = @users
  force group = users 
  create mask = 0777
  directory mask = 0777
  writable = yes
[gregorigroup]  <-- Works fine
  comment = GregoriGroup
  path = /home_media
  valid users = @users
  force group = users 
  create mask = 0777
  directory mask = 0777
  writable = yes

---

### Post by Morbius1 on 2011-05-10
What are the permissions of the shared directory:
```
ls -dl /big_part
```

---

### Post by wgregori on 2011-05-10
Now I really feel stupid... yes I had a permissions problem.  Thank you for pointing that out to me.

Wayne

---

