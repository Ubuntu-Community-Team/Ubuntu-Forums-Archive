---
title: "Mounted WebDAV share causes system to hang regularly"
date: 2012-10-26
forum: Networking &amp; Wireless
---

### Post by DigNative on 2012-10-26
Hi,

I have a remote WebDAV share mounted on my Ubuntu 12.04 LTS box using davfs2 (version 1.4.6-1ubuntu3); the connection between my computer and the remote server is stable und highly reliable. Regularly, my system begins to hang after approx. 15 minutes after the WebDAV share has been mounted.

The share isn't accessible anymore and "umount [mountpoint]" gives the following error:

```

umount: /mnt/[mountpoint]: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
umount: /mnt/[mountpoint]: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))

```

After rebooting, I can again access the share without any issues until it hangs again after approx. 15 minutes.

Probably there's an option like "ClientAliveInterval" in "/etc/ssh/ssh_config" for sshfs, but I don't know where this issue comes from and appreciate any help.

---

