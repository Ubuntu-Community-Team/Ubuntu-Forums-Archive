---
title: "Ho can I umount NFS share when the server is gone"
date: 2009-08-01
forum: Networking &amp; Wireless
---

### Post by 3Miro on 2009-08-01
Hi,

I have an Ubuntu 9.04 Desktop with running NFS server that is sharing some folders.

I have an Ubuntu 8.10 Laptop that connects to those.

Everything is running fine, I mount then I can read/write files, suspend/resume and everything works just fine.

The problem is that sometimes I just grab my suspended Laptop and go somewhere else to work and don't first umount the folders. Then when I get to the new place:

1. I cannot umount the folders. -f doesn't work and in terminal I cannot even use tab completion (on the media folder with the mounted directories)
2. If I try to suspend on the new place, the system would refuse to do that and I have to do bad shutdown (press and hold power button).

/etc/fstab has a typical line like this:
192.168.1.100:/media/Storage /media/MainStorage nfs noauto 0 0

Does anyone know what I am missing?

---

