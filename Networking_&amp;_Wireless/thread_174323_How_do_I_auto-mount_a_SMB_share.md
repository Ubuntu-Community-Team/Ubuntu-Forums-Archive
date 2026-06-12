---
title: "How do I auto-mount a SMB share?"
date: 2006-05-11
forum: Networking &amp; Wireless
---

### Post by pbb on 2006-05-11
I've got the following line in /etc/fstab:

```
//p4-3000/D /media/fat smbfs guest,uid=peter,iocharset=utf8,codepage=unicode,unicode  0  0
```

As far as I understood it, this should auto-mount the share. However, when I reboot the machine, the mount isn't there. I have to issue "sudo mount -a" to get the mount into place.

Is there anything I am overlooking? The P4-3000 machine is already running before the Ubuntu machine is booted.

(To be precise, it is actually Kubuntu running inside VMWare on the P4-3000 machine, but I don't think that should make any difference.)

---

