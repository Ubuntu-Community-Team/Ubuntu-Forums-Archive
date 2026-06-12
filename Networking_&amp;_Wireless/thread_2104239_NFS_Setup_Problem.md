---
title: "NFS Setup Problem"
date: 2013-01-12
forum: Networking &amp; Wireless
---

### Post by SnoopFogg on 2013-01-12
Hi, I'm trying to set up NFS, but I'm getting this error on the client:

russ@studio:~$ sudo mount 192.168.1.84:/home/videos /home/russ
[sudo] password for russ: 
mount.nfs: rpc.statd is not running but is required for remote locking.
mount.nfs: Either use '-o nolock' to keep locks local, or start statd.
mount.nfs: an incorrect mount option was specified

Can anyone help?  Let me know what other information would be useful.

Cheers

---

### Post by steeldriver on 2013-01-12
Have you installed the nfs-common package on the client machine?

```
$ apt-cache show **nfs-common**
Package: nfs-common
Priority: optional
Section: net
.
.
.
  Description-en: NFS support files common to client and server
  Use this package on any machine that uses NFS, either as client or
  server.  Programs included: lockd, **statd**, showmount, nfsstat, gssd,
  idmapd and **mount.nfs**.
.
.
.

```

Also are you sure you want to mount it over /home/russ (rather than a subdir e.g. /home/russ/videos)?

---

### Post by SnoopFogg on 2013-01-12
Hi, I have been following these instructions which include setting up nfs-common: [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

Also tried the suggested mount point but I get the same error.

One part of the client setup I wasn't clear on was mounting an exported subtree with this:

# mount -t nfs4 -o proto=tcp,port=2049 nfs-server:/users /home/users

Is the "nfs-server" part literally just that? Or is it the name or IP address of the server?  Similarly the instruction to mount the complete export tree with:

# mount -t nfs4 -o proto=tcp,port=2049 nfs-server:/ /mnt

---

### Post by bab1 on 2013-01-12
> **SnoopFogg said:**
> Hi, I have been following these instructions which include setting up nfs-common: [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

Also tried the suggested mount point but I get the same error.

One part of the client setup I wasn't clear on was mounting an exported subtree with this:

# mount -t nfs4 -o proto=tcp,port=2049 nfs-server:/users /home/users

Is the "nfs-server" part literally just that? Or is it the name or IP address of the server?

It should be the IP address or hostname.

You should also use mount -t nfs (not nfs4) on the latest Ubuntu versions.

---

### Post by Merrattic on 2013-01-12
This howto has always worked for me:

[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

---

### Post by bab1 on 2013-01-12
> **Merrattic said:**
> This howto has always worked for me:

[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)
The link is from 6 years ago (2006).  It may work with NFSv3 and Ubunutu 6.04.  It documents a system the is not in the current package. NFS doesn't use portmap any more for one thing.

---

### Post by SnoopFogg on 2013-01-13
Thanks everyone. Got it sorted.  I just hadn't created the mount point correctly. Everything working fine and the server mounts when it boots up.  

Cheers

---

### Post by Merrattic on 2013-01-13
> **bab1 said:**
> The link is from 6 years ago (2006).  It may work with NFSv3 and Ubunutu 6.04.  It documents a system the is not in the current package. NFS doesn't use portmap any more for one thing.

It still works regardless, the basic principles are the same. I followed the howto for my 12.04 server and workstations and **it works**. I might get round to updating it ;)

---

