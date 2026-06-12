---
title: "ssh mount in fstab"
date: 2009-05-30
forum: Networking &amp; Wireless
---

### Post by alenis on 2009-05-30
After reading several howtos I managed to mount a remote ssh share through a command looking like:

```
sshfs -o idmap=user myusername@remote:/ ~/remote
```

Everything works fine: I can even open documents with Openoffice without any trouble.

Then I tried to add a permanent mount to my fstab adding the line:

```
sshfs#myusername@remote:/ /home/myusername/remote fuse defaults,idmap=user 0 0

```

as explained in [https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)

but:
- if I try 

```
mount /home/myusername/remote
```
the answer is "only root can mount..."

- if I try 

```
sudo mount /home/myusername/remote
```

I get "read: Connection reset by peer"

What should I do to get it working?
Thanks

Edit:
Just in case somebody has the same problem, it can be solved by:
a) editing /etc/fuse.conf and uncommenting "user_allow_other";
b) using allow_other in fstab like this: sshfs#alenis@ufficio:<direcotry_to_mount> <mount_point> fuse user,allow_other 0 0

---

### Post by hotdoog on 2010-03-30
Thanks so much for posting that solution! I had the same problem and it worked for me. Someone should update that howto document.

The only difference I had is it would allow me to fstab mount (with the incorrect options given by the howto) but the mount was crazy screwed up - the file permissions were a question marks in ls... Anyway, your edit of the /etc/fuse.conf and different fstab option worked perfect for me.

Thanks so much!:KS

---

### Post by ArneBab on 2012-04-11
> **alenis said:**
> ```
sshfs -o idmap=user myusername@remote:/ ~/remote
```
&#8230;
```
sshfs#myusername@remote:/ /home/myusername/remote fuse defaults,idmap=user 0 0

```
&#8230;
Just in case somebody has the same problem, it can be solved by:
a) editing /etc/fuse.conf and uncommenting "user_allow_other";
b) using allow_other in fstab like this: sshfs#alenis@ufficio:<direcotry_to_mount> <mount_point> fuse user,allow_other 0 0

This solved my problem, thank you very much for sharing!:KS

Two additional notes: 

1. Remember the slash at the end of the folder name on the server, otherwise you get input/output errors. 
2. If you access the server via password, remember to add noauto to the options in fstab.

---

### Post by Elfy on 2012-04-11
Old thread closed.

---

