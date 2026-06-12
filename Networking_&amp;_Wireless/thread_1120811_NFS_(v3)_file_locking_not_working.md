---
title: "NFS (v3) file locking not working"
date: 2009-04-09
forum: Networking &amp; Wireless
---

### Post by beaker15 on 2009-04-09
Hi,
I have a small network with an Ubuntu server and I'm now converting all the clients from WinXP to use Ubuntu, so instead of samba i'll be using NFS for my shares. 

I've managed to get my clients to mount the NFS shares with no problems but file locking does not seem to be working. Using rpcinfo -p on the server shows all the corrcet daemons are running (portmap, nfs, mountd, status (rpc.statd),nlockmgr (rpc.lockd) and on the clients the command shows just portmap,status and nlockmgr, which i think is correct.

However, I can open the same openoffice files simultaneouly on 2 clients and make changes, which is obviously a bad thing

Can anyone help with this?

Is it worth trying to use NFS v4 instead? it looks more complex which is putting me off because i only need something simple and i think the above problem is probably an easy fix that i have missed. 

thanks

---

### Post by beaker15 on 2009-04-16
I gave up on NFS v3 and decided on NFS v4, following the guide on this site. file locking is still not working however, but I'll post a new thread

---

