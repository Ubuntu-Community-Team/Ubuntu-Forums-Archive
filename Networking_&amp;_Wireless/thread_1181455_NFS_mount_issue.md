---
title: "NFS mount issue"
date: 2009-06-07
forum: Networking &amp; Wireless
---

### Post by nkarkare on 2009-06-07
Hi,
I have a setup of 96 Kubuntu (8.04) clients connected to a CentOS server.
I have a NFS server running on CentOS and I have configured the number of NFS servers to be 16 on the server.
I am sharing a read-only NFS mount called /school/airshare. Here is the exports file dump:
*/school/airshare        *(ro,sync,no_root_squash)*

I automount this share on boot.. here is a partial dump of /etc/fstab on the Kubuntu machines:
*192.168.100.246:/school/airshare        /school nfs     defaults        0       0*

Now here is my problem:
When the clients boot up, they do not mount the NFS share (There are no warnings or errors in the message log whatsoever). Then, when I run umount -a and then mount -a, for the share to be mounted correctly.
What am I missing here?

Thanks in advance for any help!

-Nikhil.

---

### Post by dmizer on 2009-06-08
As far as I know, the asterisk (*) is not a valid character for exports.

If you want to export to an entire subnet, you'll need to do something like:
```
/school/airshare 192.168.100.0/24(ro,sync,no_root_squash,no_subtree_check)
```

Edit:
Your fstab line should look like this:
```
192.168.100.246:/school/airshare /school nfs rsize=8192,wsize=8192,timeo=14,intr
```

For more information, see the 4th link in my sig.

---

