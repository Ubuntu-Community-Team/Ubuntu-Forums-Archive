---
title: "NFS mount same directory in two places"
date: 2013-07-16
forum: Networking &amp; Wireless
---

### Post by w1ll1am on 2013-07-16
Hello all,

I am trying to mount my HTPC media drive on a frontend system with NFS. I have done this before with no problem so I am not sure what the problem is. I have two drives on my backend /HTPCmedia and /HTPCmedia2 I am mounting them with the below

```

192.168.5.6:/HTPCmedia/Videos  /storage/Videos   nfs defaults 0 0
192.168.5.6:/HTPCmedia2/Videos /storage/Videos2  nfs defaults 0 0

```
and I have the below in /etc/exports

```

/HTPCmedia/Videos       192.168.5.0/24(rw,fsid=0,insecure,no_subtree_check,async)
/HTPCmedia2/Videos      192.168.5.0/24(rw,fsid=0,insecure,no_subtree_check,async)

```

I followed this guide [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

What is happening is /HTPCmedia2/Videos is being mouted to both locations /storage/Videos and /storage/Videos2

I have checked the /etc/exports and the /etc/fstab several times and everything is right. 

So any ideas?

---

### Post by newbie-user on 2013-07-16
Did you create the /storate/Videos2 folder?

---

### Post by w1ll1am on 2013-07-16
Yes both directories exist htpcmedia2 is mounted to videos and videos2

---

### Post by papibe on 2013-07-16
Hi  w1ll1am.

It looks like the machines are in different networks: the server on 192.168.5.0 and the client on 192.168.1.0

Is that correct? May be there's an error on the export file?

Regards.

---

### Post by w1ll1am on 2013-07-17
Sorry no that was a typo. Both are on 192.168.5.0 the backend has an IP 192.168.5.6 and the frontend has an IP of 192.168.5.14.

---

### Post by papibe on 2013-07-17
Thanks.

In case the typo was in the actual /etc/exports, remember that you need to restart nfs on the server after your corrected it:
```
sudo service nfs-kernel-server restart
```
Another thought. **fsid** is used set a custom id to the filesystem being exported. It is not mandatory, but if you want to use it, don't use the same number for both exports.

Also, could you post the results of this command on the client:
```
showmount -e 192.168.5.6
```

Regards.

---

### Post by w1ll1am on 2013-07-31
> **papibe said:**
> 

Another thought. **fsid** is used set a custom id to the filesystem being exported. It is not mandatory, but if you want to use it, don't use the same number for both exports.



I changed the fsid to the UUID on each disk and now everything is working great. Thanks for the help.

---

