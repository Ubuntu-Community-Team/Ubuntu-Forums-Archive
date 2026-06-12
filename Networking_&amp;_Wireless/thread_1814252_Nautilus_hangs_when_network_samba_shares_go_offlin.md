---
title: "Nautilus hangs when network samba shares go offline"
date: 2011-07-29
forum: Networking &amp; Wireless
---

### Post by yanewby on 2011-07-29
I have a local server running Ubuntu Server 11.04 with several samba hard disks in it.  I can connect to the server from my laptop (Ubuntu 11.04) and everything runs OK until the server goes offline.

Autofs is used to mount the samba shares.

When the server goes offline something seems to go wrong, nautilus can no longer be used to browse ANY files (whether locally on my laptop or obviously on the network).  I can though access the files using terminal (eg ls $HOME).

If I type "mount" in terminal after the network has gone offline all the network drives are still there.

When I try to shutdown my PC after this happens the shutdown procedure fails and I have to do a hard power off.

If the server stays online everything works as normal.

Can someone point me in the right direction as to how to troubleshoot this?  I am new to networking/NAS/networked hard drives.

---

