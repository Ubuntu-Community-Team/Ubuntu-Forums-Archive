---
title: "Grant write permissions for Samba shares"
date: 2011-08-27
forum: Networking &amp; Wireless
---

### Post by QuinRiva on 2011-08-27
I have a Natty headless server that I would like to set up shared directories and grant specific users write permissions.  I use a Windows 2008 R2 machine with Active Directory for authentication and have created a group *GroupWithWriteAccess* which I want to have write access to the shared directory.  I want all other users to have read only access.

I have edited my smb.conf file with the following
```
[TV]
path = /media/share/Media/TV
writeable = yes
write list = primaryuser @GroupWithWriteAccess
create mode = 0660
directory mode = 0770

```

The machine is fully setup to work with Windows authentication and I can access shares from the ubuntu machine, it's just sharing local directories with the correct permissions that I can't work out.  So far I can access the files from my other machine, but I do not have write access even though I am logged on as a user who is a member of *GroupWithWriteAccess*.

Any ideas?

---

### Post by QuinRiva on 2011-08-27
Stupid me, forgot to restart Samba.

For anyone who has this problem:
sudo service smbd restart
sudo service nmbd restart

---

