---
title: "Default permissions for newly created files"
date: 2011-11-04
forum: Networking &amp; Wireless
---

### Post by mjc7373 on 2011-11-04
Hi all! 
How do I change the default file permissions when new files are created by users? The files are on the server in an ext3 partition, accessed by Windows PCs via Samba. When users create files the defaull permissions are rw-r--r--. I want the default permissions to be is: rwxrwx---. 

In smb.conf, I have set file creating mask to 0755:

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
   create mask = 0775

Even when I ssh into the server and use touch to create a test file, the same unwanted default permissions are set. Any insight would be greatly appreciated. Thanks!

---

