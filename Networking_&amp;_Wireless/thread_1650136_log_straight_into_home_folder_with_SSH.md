---
title: "log straight into home folder with SSH"
date: 2010-12-21
forum: Networking &amp; Wireless
---

### Post by Ceiber Boy on 2010-12-21
when my restricted users log into their accounts remotely i want them to only be able to see their own account and not the root directory or any other account.

I've used the groups and users settings and seam unable to configure this!

How is this done?

Thanks

---

### Post by SeijiSensei on 2010-12-21
There are many parts of the root filesystem that all users can see, /usr/bin being a good example.  You can't really restrict them from these places, but the security model in Linux doesn't let them make changes to any of them either.

If your real concern is restricting each user from seeing other users' files, then just make sure that each user's home directory (/home/user) has 0700 permissions.

If you really want to keep users out of the main root directory, you'll have to consider using [chroot]("http://blogs.techrepublic.com.com/opensource/?p=229").  This is a major pain in the neck, however, since each user will then need to have a skeleton version of the root filesystem in his or her home directory.  These replicated root filesystems must contain all the necessary files and directories they'll need to make all applications they use work correctly.  That means, for instance, that each user running OpenOffice would need to have a complete installation of OO.org in his or her home directory.

---

### Post by Ceiber Boy on 2010-12-21
> **SeijiSensei said:**
> There are many parts of the root filesystem that all users can see, /usr/bin being a good example.  You can't really restrict them from these places, but the security model in Linux doesn't let them make changes to any of them either.

If your real concern is restricting each user from seeing other users' files, then just make sure that each user's home directory (/home/user) has 0700 permissions.

If you really want to keep users out of the main root directory, you'll have to consider using [chroot]("http://blogs.techrepublic.com.com/opensource/?p=229").  This is a major pain in the neck, however, since each user will then need to have a skeleton version of the root filesystem in his or her home directory.  These replicated root filesystems must contain all the necessary files and directories they'll need to make all applications they use work correctly.  That means, for instance, that each user running OpenOffice would need to have a complete installation of OO.org in his or her home directory.
Each user account would be used as a file system for remote access to read write files to their individual user account, no execution or running of applications, i therefore assume this would be easier to accomplish!

with that in mind would it be possible to just restrict them to their own home directory over a ssh login?

---

### Post by SeijiSensei on 2010-12-21
> **Ceiber Boy said:**
> Each user account would be used as a file system for remote access to read write files to their individual user account, no execution or running of applications, i therefore assume this would be easier to accomplish!

with that in mind would it be possible to just restrict them to their own home directory over a ssh login?

A better solution would be to share their home directories with NFS or Samba, or have them use (S)FTP.  There's no need for them to use SSH since they don't need to run shells on the server.

---

