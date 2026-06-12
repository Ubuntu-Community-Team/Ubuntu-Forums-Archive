---
title: "gnomebaker failed, now cd drive is stuck"
date: 2008-05-16
forum: Multimedia Software
---

### Post by prshah on 2008-05-16
Hello,

I was trying to burn a CD using GnomeBaker. It didn't complete successfully, and I realized why, so that's not the issue.

When I try to eject the failed medium, it doesn't eject. I pressed the eject button; no response. I right-clicked and chose eject off the places menu entry ("Blank CD-R disc") and it didn't respond. I used sudo eject and no dice.

```

Fri May 16 23:52:21 ~:$ sudo eject -v /dev/cdrom1
eject: device name is `/dev/cdrom1'
eject: expanded name is `/dev/cdrom1'
eject: `/dev/cdrom1' is a link to `/dev/scd0'
eject: `/dev/scd0' is not mounted
eject: `/dev/scd0' is not a mount point
eject: `/dev/scd0' is not a multipartition device
eject: trying to eject `/dev/scd0' using CD-ROM eject command
eject: CD-ROM eject command failed
eject: trying to eject `/dev/scd0' using SCSI commands
eject: SCSI eject succeeded

```

Though it says SCSI eject succeeded, nothing has happened. 

A restart later, everything was fine.

This is the nth time such a problem has occurred; the drive seems to be "stuck" for want of a better word.

It's not a hardware problem; occurs only after a failed GnomeBaker burn, though not always. When in general use, never a problem.

Any suggestions for:

a) A graceful recovery (ie, not having to restart)
b) A prevention?

---

### Post by gandaran on 2008-05-16
if the failure is due to a gnomebaker error, you can try by just deleting the hidden home gnomebaker folder, start gnomebaker again and everything should be back to normal.
the gnomebaker configuration folder is either in home/user/.gnomebaker or /home/user/.gconf/apps, I don't know for sure as I don't use gnomebaker.

gandaran

---

