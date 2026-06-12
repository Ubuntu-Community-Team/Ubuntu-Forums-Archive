---
title: "NFS with Ubuntu Client and OS X Server"
date: 2011-11-08
forum: Networking &amp; Wireless
---

### Post by bencpeters on 2011-11-08
Hi all, I'm trying to set up a NFS share between an OS X host and an Ubuntu Desktop virtual machine under parallels. I've set up the share on OS X by editing the '/etc/exports" file, and it appears on both OS X and Ubuntu with "showmount -e HOSTIP". However, when i try to connect to it from Ubuntu, I get the following: 

```
sudo mount -vt nfs 192.168.1.6:/Users/user/NFS ~/Desktop/NFSMount

mount.nfs: timeout set for Tue Nov 8 18:56:06 2011
mount.nfs: trying text-based options 'vers=4,addr=192.168.1.6,clientaddr=10.211.55.6'
mount.nfs: mount(2): Protocol not supported
mount.nfs: trying text-based options 'addr=192.168.1.6'
mount.nfs: prog 100003, trying vers=3, prot=6
mount.nfs: trying 192.168.1.6 prog 100003 vers 3 prot TCP port 2049
mount.nfs: prog 100005, trying vers=3, prot=17
mount.nfs: trying 192.168.1.6 prog 100005 vers 3 prot UDP port 911
mount.nfs: mount(2): Permission denied
mount.nfs: access denied by server while mounting 192.168.1.6:/Users/benpeters/NFS

```

For testing purposes, I've set the server up without network/mask restrictions, and showmount lists it as being available to everyone.

any ideas?

thanks!

---

### Post by SeijiSensei on 2011-11-08
You're trying to mount as root.  Does the server have no_root_squash as an option in /etc/exports?

Here's a bit about root_squash from "man exports":

> 
root_squash
Map requests from uid/gid 0 to the anonymous uid/gid.


Usually that's the default unless no_root_squash is specified as an option on the share definition in /etc/exports.

---

