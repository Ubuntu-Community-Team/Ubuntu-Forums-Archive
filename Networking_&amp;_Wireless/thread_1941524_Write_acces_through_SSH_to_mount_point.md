---
title: "Write acces through SSH to mount point"
date: 2012-03-15
forum: Networking &amp; Wireless
---

### Post by jorants on 2012-03-15
Hey everyone,

my server runs openSSH, witch is use for SSHFS connections, witch works great, i can read and write everything in my home dir.
so, i just installed a new hard drive in my ubuntu server setup.
i mounted it to /home/user/disk so i can acces it trough sshfs, witch shows my home dir.
now the problem is, i can see all the files and del/create folders, but i cant move files from my home dir to my mounted disk (by dragging and dropping) and i can not delete a dir witch contains something.

I dont really get wy i'm premitted to move stuff on the drive and in my home bu not between the two?

maby usefull, my fstab entry:
```

/dev/sdb1       /home/joran/disk        ntfs-3g rw,umask=000,dmask=000,user,owner   0   0

```

tanx in advance

Joran

---

