---
title: "Samba second drive share issue"
date: 2011-02-12
forum: Networking &amp; Wireless
---

### Post by voicesinthefan on 2011-02-12
Howdy.  I recently installed ubuntu on one of my computers and am trying to get all my sharing worked out so I can access stuff with my windows machine.  I'm still very stupid when it comes to linux.

Setting up sharing with Samba, I got my /home/user/media folder to share just fine.  However I made a folder located on my second drive that I would like to share.

I have this entry for it in my smb.conf 

```
[80GBshare]
   comment = /media/Sifl_80GB/Shared/ folder share
   path = /media/Sifl_80GB/Shared
   browsable = yes
   guest ok = no
   read only = no
   create mask = 0770
```

the second drive is mounted on /media/Sifl_80GB and it was formatted as ext4.

My windows machines see the 80GBshare entry but I get the error "network path not found" when I try to open the folder.  Does this mount need to be listed in my fstab for this to work correctly?  I'm noticing something in the comments of the smb.conf for auto-mounting a cdrom drive when a cdrom drive is accessed by adding a fstab entry, so I'm wondering if this needs to be done with my second drive?

---

### Post by Morbius1 on 2011-02-12
"network path not found" almost sounds like a Linux file permissions issue.

The entire path has to allow "others" to access.

So if you do a:
```
 ls -al /media/Sifl_80GB
```Make sure the entire path to /media/Sifl_80GB/Shared allows the remote user to access the share.

---

### Post by voicesinthefan on 2011-02-12
/media/Sifl_80GB/Shared has the same permissions as my /home/user/media folder that works just fine.

I have permissions set to allow user and group read and write, but not others.  I created a separate user that I could log in with my windows machine, and I changed the group of the two shared folders to a group containing both my ubuntu user and the windows machine user.

And I just changed the permissions on /media/Sifl_80GB/Shared to o+rx and still got the same network path not found.

---

### Post by dmizer on 2011-02-12
Do you have an /etc/fstab entry for the second drive?

If so, please post the contents of /etc/fstab

---

### Post by dmizer on 2011-02-12
> **voicesinthefan said:**
> Does this mount need to be listed in my fstab for this to work correctly?
Yes, the second drive will need to have an /etc/fstab entry in order for you to share it correctly.

---

### Post by voicesinthefan on 2011-02-12
Thanks! Got it!

---

