---
title: "cifs mounted folder is read-only"
date: 2012-06-04
forum: Networking &amp; Wireless
---

### Post by tomaspecserke on 2012-06-04
Hello,

I'm trying to mount cifs folder in RW mode, but each time I try to write, I get permission denied.

fstab:
```
//host/folder /moutn-point cifs username=***,password=***,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```

Solution with credentials fie edoesn't work either.
Any suggestions?

Thanks.

---

### Post by jobsonandrew on 2012-06-04
Hi, I recently had to do this too and it took some playing around. Here's an entry from fstab that mounts a cifs share in my network RW:
```
//pandora/xbmc/thumbnails /home/revo/.xbmc/userdata/Thumbnails cifs _netdev,defaults,noperm,domain=pandora,credentials=/home/revo/.smbcreds 0 0
```
I couldn't tell you what each of the options mean in detail but you can look them up. the domain is just the hostname of the server in this example

I hope it helps

---

### Post by tomaspecserke on 2012-06-05
Thanks, that did it!

---

