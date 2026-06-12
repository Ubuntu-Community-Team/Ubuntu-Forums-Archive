---
title: "whats wrong with fstab entry to mount lan directory"
date: 2010-08-18
forum: Networking &amp; Wireless
---

### Post by walter_j on 2010-08-18
//192.168.1.99/home/public /mnt/server cifs credentials=/etc/cifspw,uid=root,iocharset=utf8,codepage=unicode,unicode  0  0

the above entry returns mount error 6. I can ssh to the pc, but i can't mount it or get it working in stab. apt-get returns samba, smbfs, and smbclient is already at newest version.

---

### Post by theozzlives on 2010-08-18
you wanna do:

```
//server/share /mountpoint cifs credentials=/path/file defaults 0 0
```

I'm pretty sure that'll work.

---

### Post by walter_j on 2010-08-19
> **theozzlives said:**
> you wanna do:

```
//server/share /mountpoint cifs credentials=/path/file defaults 0 0
```

I'm pretty sure that'll work.

thanks for your pointer. I confused share with directory name. the share is defined in smb.conf. The share mounts now. Linux is so cool...

---

