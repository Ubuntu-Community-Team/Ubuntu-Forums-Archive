---
title: "Samba :share  directory to be writeable by certain users only ?"
date: 2009-09-11
forum: Networking &amp; Wireless
---

### Post by uncle-c on 2009-09-11
Just fiddling about with my Samba server and I was wondering what would be the best way to set up the share so user1 has read/write/execute access to the share and user2 only has read access ? I've been trying to alter some settings in my smb.conf file but none seem to have worked. Everything is set up fine all users can login with their unique passwords and can create/delete files on the share. However I would like certain users to be restricted read access. Perhaps the permissions on the share directory need to be changed ? The share directory is owned by root and  group  is "share." All users have "share" as their secondary group, hence they can access the share.

```
drwxrwx---  2 root   share  4096 2009-09-11 17:50 share
```

thanks,
C

---

### Post by uncle-c on 2009-09-11
Sorted - just added the "read list" line.

Just an aside , if the directory is r-x permissions for group then why would the smb.conf  line  "write list = user1 " still not allow write access to user1 ? I thought the "write list" line adds write functionality to a read only share ?

c

---

### Post by Iowan on 2009-09-11
I'd need to check my reference books, but I thought Samba could only *tighten* permissions from Linux settings (but could adjust it's own restrictions) - so a "write list" could override a "read only=yes" option, but not a directory permission. So the share could be tagged "read only", but those on the "write list" could still write to it. Conversely, those on the "read list" could not write - even if the directory was 777.
But I've been wrong before...

---

### Post by uncle-c on 2009-09-11
Thanks Iowan. I've been messing about with smb.conf settings and read/write permissions all day and what you say sounds about right. I've found that directory permissions definitely cannot be overriden no matter what is contained in your smb.conf file.

---

