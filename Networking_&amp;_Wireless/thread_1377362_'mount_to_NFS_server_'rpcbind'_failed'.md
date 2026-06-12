---
title: "'mount to NFS server 'rpcbind' failed'"
date: 2010-01-10
forum: Networking &amp; Wireless
---

### Post by Bucky Ball on 2010-01-10
Hi all.

Trying to mount /media from server to /media/Lounge on client using NFS. When issue:

```
anna@katie:~$ sudo mount -a
[sudo] password for anna: 
mount.nfs: mount to NFS server 'rpcbind' failed: RPC Error: Program not registered
mount.nfs: internal error

```... is what I get.

I setup my laptop as a server with the help of this guide:

[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

... awhile ago. After a little tweaking I got it working beautifully. My laptop died though and my wife just bought another. I have setup one of the desktops as the server and the new laptop as a client. I have gone through the guide several times and all seems to be in order but maybe I'm missing something.

192.168.0.100 = server
192.168.0.104 = client

Can somebody fill me in on what is causing the particular error above? Am using Hardy 8.04.3 LTS

*** All seems to be working now.

---

### Post by johnson.d on 2010-01-12
1) You can Disable both iptables and Apparmor for testing purpose in both client and the server
2) If it is working then we can enable them with suitable configurations.

---

### Post by Bucky Ball on 2010-01-12
> **Bucky Ball said:**
> 

*** All seems to be working now.

.

---

