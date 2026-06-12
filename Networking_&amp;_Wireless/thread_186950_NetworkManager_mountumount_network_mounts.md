---
title: "NetworkManager mount/umount network mounts"
date: 2006-06-02
forum: Networking &amp; Wireless
---

### Post by el3ktro on 2006-06-02
Hello,

I want to connect my two Ubuntu machines via NFS/Samba/SHFS or whatever. One of them is a laptop, and it does not always have a network connection. The problem with "statically" mounting a network share in /etc/fstab is of course when there's no network connection. I have installed NetWorkManager on the iBook, which correctly detects and switches my cable & wireless connection. So I'm wondering, is there a way to let NetWorkManager run a mount/umount script which would mount the remote directory when there is a network connection, and umount it when there's no connection? Or is there some kind of mounting applet for Gnome where I could just mount/umount the remote dir with a single mouse click?

I'd very much prefer to use VFS instad, but unfortunately many apps don't know how to handle this VFS stuff, which honestly really sucks because VFS is such a great thing especially with Nautilus :-(

Tom

---

