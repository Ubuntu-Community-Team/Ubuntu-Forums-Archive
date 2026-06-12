---
title: "Convert manual mount to auto mount in fstab"
date: 2006-07-14
forum: Networking &amp; Wireless
---

### Post by manfrommonroe on 2006-07-14
I was able to create a mount (read & write) to a WinXP shared folder on another pc with this:

sudo mount -t smbfs -o username=rich,gid=users,dmask=777,fmask=777,rw //immanuel/SharedDocs /mnt/immanuel/

How would I convert this to the fstab or do I have to do it through samba?

Thanks!

---

### Post by ciscosurfer on 2006-07-15
It's not advisable to make your WinXP folder mount read/write.  Doing so can have serious consequences.  However, you can mount a Samba share (which gets called by smbmount, not mount)...I would suggest doing a```
man mount
```and looking at the nfs section as well as the smbfs section.

---

