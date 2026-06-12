---
title: "sshfs load on boot"
date: 2009-02-08
forum: Networking &amp; Wireless
---

### Post by pfwd.tech on 2009-02-08
Hi 
How do I start this sshfs at start up? 
```
sshfs#<user>@<ip>:/media/backup   /media/backup   fuse    users,allow_other,uid=1000,gid=1000,umask=000   0       
```
I'ts a fat32 share on  my server

Each time I boot I have to do the following
```
sudo mount -a 
```
Then enter my local machines password and then my host user password

Is this done via a ssh key or something? Does anyone know of a good tutorial on this?

---

### Post by pfwd.tech on 2009-02-10
I managed to get this working by using this post as a guide
[http://ubuntuforums.org/showthread.php?t=896474](http://ubuntuforums.org/showthread.php?t=896474)

---

