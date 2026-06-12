---
title: "Mount error(12) and I"
date: 2009-10-09
forum: Networking &amp; Wireless
---

### Post by TheChaos0 on 2009-10-09
Right, so this annoying error has cropped up. I'm trying to share my NTFS drive so my Ubuntu laptop can read it.

When I try to mount it on the laptop I get mount error 12 cannot allocate memory. After looking around it turned out not to be the usual problem with Windows - NT_STATUS_INSUFF_SERVER_RESOURCES. Instead the error is - CIFS VFS: cifs_read_super: get root inode failed.

I can mount the ex2/3/4 partitions just fine but NTFS won't budge in!!

Any help would be appreciated. I spent like 2 hours on google but to no avail.

Thanks in advance!

---

### Post by TheChaos0 on 2009-10-10
Anyone? I'm also having this problem Linux-to-Linux, with the same NTF drive.

---

### Post by TheChaos0 on 2009-10-10
OK, I have fixed Linux-to-Linux issue. My ntfs drive was not mount read-write.

I have create a new user with a password in Windows 7 and now I can mount the windows share manually using:

```
sudo mount - cifs //WINPC/diske -o username=Myname password=mypass /media/lan/diske
```

However, I can only write on the share as a root, no user write access. 

I still cannot mount it from Places/Network/WinHostName. It does not accept username/password of the Windows 7 account.

Any help will be appreciated.

---

### Post by alexandermdevereux on 2009-10-10
you could also try sudo nautilus to open the share for easier file transfers

---

### Post by foxy123 on 2009-10-11
> **alexandermdevereux said:**
> you could also try sudo nautilus to open the share for easier file transfers
I do not think that it is good idea to use sudo with nautilus.

---

### Post by lensman3 on 2009-10-11
Look at the man page for mount.cifs, "man mount.cifs" from the command line.  You need to set the "uid" and "gid" options.  Make it the same as the user who will use it.  You get a persons uid "user id" from the 3rd field of the /etc/passwd file and the gid from the 4th field.  You might also have to set the rw option.

---

