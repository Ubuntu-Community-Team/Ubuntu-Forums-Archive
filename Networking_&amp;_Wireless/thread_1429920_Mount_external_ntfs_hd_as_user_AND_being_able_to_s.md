---
title: "Mount external ntfs hd as user AND being able to share"
date: 2010-03-14
forum: Networking &amp; Wireless
---

### Post by VCoolio on 2010-03-14
I have an ntfs external hd; I can mount and use it fine, without entry in fstab, but not share stuff. That is to say: I can use nautilus / thunar to share folders on it without errors, but they are not accessible via the network. The issue may be that the mount point has permissions 700. I can solve that by 
```
sudo mount -t ntfs-3g /dev/sdb1 /media/Databank -o umask=0,nls=utf8
```
or by setting umask=022 in fstab, but then I can't mount it as user anymore; if I set fstab to
```
/dev/sdb1       /media/Databank ntfs-3g user,umask=022,nls=utf8,defaults 0 0
```
I get this when I try to mount it as user in the filebrowser:
```
Error mounting: mount exited with exit code 1: helper failed with:
Unprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated FUSE
support and make it setuid root. Please see more information at 
http://ntfs-3g.org/support.html#unprivileged
```

The hints at [http://www.tuxera.com/community/ntfs-3g-faq/#unprivileged](http://www.tuxera.com/community/ntfs-3g-faq/#unprivileged) I don't understand. Ideas on how to be able to both mount as user and share stuff on it? I'm on karmic btw.

---

### Post by gwath on 2010-12-29
Is there any solution for this problem yet?

I have searched for hours...

---

