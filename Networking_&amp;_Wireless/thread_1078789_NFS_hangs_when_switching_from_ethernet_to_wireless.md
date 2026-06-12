---
title: "NFS hangs when switching from ethernet to wireless"
date: 2009-02-23
forum: Networking &amp; Wireless
---

### Post by hannes2000 on 2009-02-23
hello,

I use NFS to share files using intrepid server, and mount these shares on my laptop (intrepid Desktop). 

excerpt from fstab:
```

jaco:/home/hannes/media /media/jaco_media nfs rw,user 0 0
jaco:/home/hannes/media/audio /home/hannes/audio nfs rw,user 0 0

```

everything works fine, until I unplug the ethernet cable from my laptop. NetworkManager then automatically switches to wireless, and every application trying to access those mounted folders hangs. "NFS: server jaco not responding"-entries appear in syslog. After 5-10 minutes, things start working again, and "NFS: Server jaco ok" is written to syslog. While "NFS hangs", I can ssh/ping to the server without any problems. I tried restarting nfs-common and nfs-kernel-server on both the laptop and the server, but nothing helps except plugging the cable back in, waiting or rebooting the server. If I unmount the shares before unplugging the cable (edit: and then remount them), the problem doesn't occur. 

While I would understand that I cannot seamlessly preserve the connection, being able to reset it instead of waiting or rebooting would be nice nonetheless. Is there any way I can do that?

Cheers
 Hannes

---

