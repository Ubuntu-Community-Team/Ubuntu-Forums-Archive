---
title: "Rights samba files"
date: 2011-05-12
forum: Networking &amp; Wireless
---

### Post by PaulNL on 2011-05-12
Hello all,

I have a server with i have installed Samba but now i have a strange problem. When a user changes a file a other user can't access it afterwards.

So i have user X and Y both are from the group Data when User X opens a file and save it again user Y can't open it. De file had as group settings administrator:Data after User X safes the file the group was changed to X:users.

How can i change samba so it keep the als user groups ??

Paul

---

### Post by kerfurdt on 2011-05-12
In smb.conf you can use the 'force user =' or 'force group =' option on the share definiton.  This is from my smb.conf:

[sys]
path = /srv/samba/domain/sys
browseable = yes
writable = yes
read only = No
force group = sambashare
vfs object = recycle
recycle:repository = /srv/samba/domain/.sys_undelete
recycle:directory_mode = 0777
recycle:keeptree = Yes
recycle:versions = Yes
recycle:touch_mtime = Yes
dos filemode = Yes
inherit acls = Yes

After initiating the change my users weren't stepping on each other's toes anymore.  In my example /srv/samba and all of its subdirectories are owned by the sambashare group.

---

### Post by PaulNL on 2011-05-13
Thanks for the help.

But now i use the ACL option but i can't force new files and folder to be in a specific group.

Paul

---

