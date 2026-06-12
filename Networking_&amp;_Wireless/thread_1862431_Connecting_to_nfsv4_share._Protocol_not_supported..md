---
title: "Connecting to nfsv4 share. Protocol not supported."
date: 2011-10-16
forum: Networking &amp; Wireless
---

### Post by GROwen on 2011-10-16
Hi all,

I'm attempting to connect to an NFS server (Mac OS X 10.7) using the method;
```

# mount -t nfs4 -o proto=tcp,port=2049 nfs-server:/ /mnt
```listed here - [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

But I get the error 

> mount.nfsv4 error: Protocol not supportedWhen I use the following mount command;

```
#mount -t nfs nfs-server:/ /mnt
```It seems to work fine.

Should I be concerned that it's not working with the first mount command or that it's not an optimised connection with the second?

Thanks in advance,

---

### Post by GROwen on 2011-10-18
bump.

Any suggestions on where I could find some nfsv4 boffin assistance?

---

