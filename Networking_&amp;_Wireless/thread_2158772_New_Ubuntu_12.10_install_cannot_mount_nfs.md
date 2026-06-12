---
title: "New Ubuntu 12.10 install cannot mount nfs"
date: 2013-06-30
forum: Networking &amp; Wireless
---

### Post by ravalox on 2013-06-30
I have a new install of 12.10; I have a new synology ds212j nas solution I'm trying to mount on it.  My laptop has an install of 12.10 from months ago- the laptop can mount my NFS share with no trouble; my newly installed media center cannot seem to find the very same nfs mount.  I've installed nfs-common, I even tried nfs-kernel-server, nothing.  When I attempt to mount it sits for a while then times out.  I know this can't be a nas configuration problem because this works on my laptop- I've googled all these guides online, tried all of them and I still cannot mount this shared folder.  Any ideas?

---

### Post by gordintoronto on 2013-07-01
Have you read this:
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---

### Post by ravalox on 2013-07-01
I did, same issue- hangs until it times out.  Oddly I can ping the nas solution, I just can't nfs into it.

---

### Post by steeldriver on 2013-07-01
are the exports visible using showmount? e.g.

```
showmount -e 192.168.1.127
```

---

