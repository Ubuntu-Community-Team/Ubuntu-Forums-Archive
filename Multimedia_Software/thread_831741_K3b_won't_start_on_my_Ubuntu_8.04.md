---
title: "K3b won't start on my Ubuntu 8.04"
date: 2008-06-17
forum: Multimedia Software
---

### Post by driesel on 2008-06-17
Hi,

I've got a problem with K3b running on Ubuntu 8.04.
It runs just fine when I load it as root, but I can't get it to start under my normal user account.
I get this when I try to start K3b from the terminal:

```

trying to create local folder /home/driesel/.kde/share: Permission denied
trying to create local folder /home/driesel/.kde/share: Permission denied
trying to create local folder /home/driesel/.kde/share: Permission denied
trying to create local folder /home/driesel/.kde/tmp-dries-laptop: Permission denied
trying to create local folder /home/driesel/.kde/share: Permission denied
trying to create local folder /home/driesel/.kde/share: Permission denied
startkdeinitlock: WARNING: KTempFile: Error trying to create /home/driesel/.kde/tmp-dries-laptop/startkdeinitlockXXXXXX.tmp: Permission denied
startkdeinitlock: WARNING: KTempFile: Error trying to create /home/driesel/.kde/tmp-dries-laptop/startkdeinitlockXXXXXX.tmp: Permission denied
startkdeinitlock: WARNING: KTempFile: Error trying to create /home/driesel/.kde/tmp-dries-laptop/startkdeinitlockXXXXXX.tmp: Permission denied
startkdeinitlock: WARNING: KTempFile: Error trying to create /home/driesel/.kde/tmp-dries-laptop/startkdeinitlockXXXXXX.tmp: Permission denied
startkdeinitlock: WARNING: KTempFile: Error trying to create /home/driesel/.kde/tmp-dries-laptop/startkdeinitlockXXXXXX.tmp: Permission denied
startkdeinitlock: WARNING: KTempFile: Error trying to create /home/driesel/.kde/tmp-dries-laptop/startkdeinitlockXXXXXX.tmp: Permission denied
trying to create local folder /home/driesel/.kde/share: Permission denied
trying to create local folder /home/driesel/.kde/share: Permission denied
trying to create local folder /home/driesel/.kde/share: Permission denied
trying to create local folder /home/driesel/.kde/socket-dries-laptop: Permission denied
trying to create local folder /home/driesel/.kde/socket-dries-laptop: Permission denied
kdeinit: Aborting. bind() failed: : Permission denied
Could not bind to socket '/home/driesel/.kde/socket-dries-laptop/kdeinit__0'
startkdeinitlock: ERROR: KUniqueApplication: Can't setup DCOP communication.

```

How can I grant permissions to my account in order to run K3b? (note: K3b seems to be the only troublesome app)

greetz,
driesel

---

### Post by argail1980 on 2008-06-17
have you started it as root at first? check the read/write permissions for that folder..

(nautilus: right click on folder > properties > permissions)

also post the output of
```
groups driesel
```
maybe you have to add yourself to a group that is allowed to use the cd-writer

---

### Post by Nikitas350 on 2008-06-17
Try running this command on terminal:
sudo chown driesel /home/driesel/.kde
sudo chmod -R a+rwx /home/driesel/.kde

---

### Post by driesel on 2008-06-17
```
driesel@dries-laptop:~$ groups driesel
driesel adm dialout cdrom floppy audio dip video plugdev fuse lpadmin admin

```

My /home/driesel/.kde folder seems to be root owned indeed.

---

### Post by driesel on 2008-06-17
OK, problem solved already!

---

### Post by argail1980 on 2008-06-17
mark the thread as solved please

---

