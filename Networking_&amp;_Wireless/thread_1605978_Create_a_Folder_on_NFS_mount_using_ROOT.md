---
title: "Create a Folder on NFS mount using ROOT?"
date: 2010-10-26
forum: Networking &amp; Wireless
---

### Post by csharpplus on 2010-10-26
I have a network drive that is mounted using the following entry in 'fstab':

```

192.168.0.254:/media/data_center/internet_backup/    /home/aa/internet_backup    nfs    rw,soft,intr    0    0

```

For some reason, when trying to create a new directory in '/home/aa/internet_backup/' as ROOT, the operation fails due to 'permissions':

```

aa@internet:~$ ls internet_backup/
aa@internet:~$ sudo mkdir internet_backup/new_dir
mkdir: cannot create directory `internet_backup/new_dir': Permission denied
aa@internet:~$ 

```

The same command (of creating 'new_dir') works perfectly when I do it using user 'aa' (without 'sudo'). 
What can I do to also allow 'root' to create 'new_dir' (and other directories)?

Thanks in advance.

---

### Post by amauk on 2010-10-26
do you have root_squash in the NFS server's /etc/exports file?

---

### Post by csharpplus on 2010-10-26
Hi amauk,

I tried both ways and it didn't work. am I supposed to have it?

---

