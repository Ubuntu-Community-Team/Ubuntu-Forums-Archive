---
title: "Mounting NFS shares on NAS"
date: 2012-11-10
forum: Networking &amp; Wireless
---

### Post by holiday on 2012-11-10
10.04 and a Patriot Javelin S4 with UNIX filesharing enabled. I understand that means NFS.

I've installed nfs-common, created /etc/nfs-common with:
NEED_IDMAPD=yes
NEED_GSSD=no # no is default

# showmount -e fs

Shows the NAS shares, but when I try to mount one of them, the server denies permission.

The server requires some authentication. Using IDMAPD transmits the username, I guess, and my username matches the name on the server. All should be well except that only root can make mount requests, and the server doesn't know root. Shouldn't have to. Root is strictly a local account. 

A little lost here. Google says there's no way to send a username with a mount request, but then what's the IDMAPD all about. 

Links welcome.

Thanks.

---

### Post by luvshines on 2012-11-12
> **holiday said:**
> 
Shows the NAS shares, but when I try to mount one of them, the server denies permission.

How are you trying to mount the shares ?


> All should be well except that only root can make mount requests, and the server doesn't know root. Shouldn't have to.
Yes, only root can mount the shares

> A little lost here. Google says there's no way to send a username with a mount request, but then what's the IDMAPD all about.
NFS mounts are always host based, ie that based up client's IP. The NFS share definition defines which client IPs are allowed to mount.
Root user on any of the allowed client mounts the share and for no particular user.
Any logged in user who wishes to access the mount point need to have valid permissions on the share. During this permissions validation, the IDMAPD may come into picture

Does that make sense ? In the above explanation I am assuming no kerberos is used

---

### Post by holiday on 2012-11-17
Solved the problem by mounting the share with the user option.

In /etc/fstab:

//nas/holiday/ /home/holiday/fs ext4 auto,owner,user

where:
- nas is the /etc/hosts name for the NAS IP, and
- I have previously created /home/holiday/fs 

Works like a charm.

I am disappointed that performance does not appear better than Samba.

---

