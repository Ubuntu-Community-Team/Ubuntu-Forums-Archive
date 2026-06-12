---
title: "Problem with NFS share mounting"
date: 2010-12-28
forum: Networking &amp; Wireless
---

### Post by buzai.andras on 2010-12-28
Hi all,

I have some problems related to mounting a NFS share.
I have the following setup:
 1. NFS Server (FreeNFS from "http://sourceforge.net/projects/freenfs" running on Window 2003 Server - I can't change the OS)
 2. NFS Client on Ubuntu 9.10 Server
 3. NFS Client on Ubuntu 10.04 Desktop

Both Ubuntu installations contain no custom packages. 
On both Ubuntu installations nfs-common (and dependencies) was installed from the official ubuntu package repository (karmic for 9.10 and lucid for 10.04).
There are no firewalls in the setup (for testing all firewalls were disabled).

Here is my problem:
I **can **mount the NFS shares on the Ubuntu 9.10 server machine, but **NOT **on the Ubuntu 10.04 Desktop machine.

On the Ubuntu 10.04 machine I get the following error: "**Permission denied**".
On both nfs clients the mount is executed as root.
I use the following mount command:
    *mount -t nfs -o rw,nfsvers=3,rsize=32768,wsize=32768,udp,nolock,hard SERVER-IP:/ /mnt/nfs -v*

Here is the output of the command on Ubuntu 10.04:

   [I] mount.nfs: timeout set for Wed Dec 29 00:16:58 2010
    mount.nfs: text-based options: 'nfsvers=3,rsize=32768,wsize=32768,udp,nolock,hard,addr=SERVER-IP'
    mount.nfs: mount(2): Permission denied
    mount.nfs: access denied by server while mounting SERVER-IP:/
[/I]

Any ideas why is this working properly every time on Ubuntu 9.10 but it DOESN'T work on Ubuntu 10.04?

Thank you,

Buzai

---

