---
title: "samba questions"
date: 2006-05-01
forum: Networking &amp; Wireless
---

### Post by RyanGT on 2006-05-01
I have two samba questions.  First, where does ubuntu auto-mount the samba shares to?  I have a share in windows that I can find using Places->Network Servers and browsing through Nautilus, but I need to access it through the shell and can't find the mount point.

Second, where should I start trying to trouble shoot why my Ubuntu machine can see and access my windows shares without a problem, but my windows machine can't see or access any of the linux shares.  Both firewalls are turned off.

Thanks,

Ryan

---

### Post by Jason_25 on 2006-05-01
/media is where you should look for mounts.  The [code]mount[code] command will list all mounts.

/var/log/samba is where you should go for samba troubleshooting.

---

### Post by RyanGT on 2006-05-01
I can see the windows folder in Nautilus, but there is no corresponding folder in /media.

---

### Post by Jason_25 on 2006-05-02
You'll probably want to mount the samba share the normal way then.

---

### Post by RyanGT on 2006-05-02
o.k. then how do I find the path to type into smbmount?  I tried smbtree and it seemed to give me the right root, but I can't seem to mount that root (or the folders that are under it).

---

### Post by Jason_25 on 2006-05-02
```

smbclient -L ipofsambahost

```

Also, I wouldn't use smbmount.  Mount it like you would with anything else.  Either through the fstab or with
```

mount -t smbfs -o username=shareusername //remote/directory /local/directory

```

---

### Post by RyanGT on 2006-05-02
o.k.  Thanks.  I was able to mount the folder with

sudo mount -t smbfs //192.168.0.105/thesis temp

Now the next thing I need to do is leave the folder mounted, but still be able to edit files in windows.  I need to use speach recognition software to edit files in windows, but afer I edit them I need to run them as python files in linux.  So, I want to edit them in windows and quickly be able to execute them in Linux.  It seems like mounting the folder in Linux has made the files read-only in windows.

Any thoughts on that?

Thanks,

Ryan

---

### Post by RyanGT on 2006-05-02
Actually, it seems to work o.k. if I have the file open in windows before I mount the folder in Linux.

Thanks again,

Ryan

---

