---
title: "mount curlftpfs end exports"
date: 2013-03-08
forum: Networking &amp; Wireless
---

### Post by camelseller on 2013-03-08
Hello,
 I created a folder as a normal user

```
/media/ftp     p2p:users

```
I mounted it using the command:

```
curlftpfs -o allow_other [ftp://217.147.232.18/pub/](ftp://217.147.232.18/pub/) /media/ftp/
```

and then I noticed that the /media/ftp/ folder, become root-owned

```
/media/ftp     root:root
```

Then if I try to export /media/ftp/ via nfs I get always [access denied] from the other lan hosts.

What am I doing wrong?

Please can someone help me to export a curlftpfs-mounted-folder via nfs or cifs?

thankyou!

---

