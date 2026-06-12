---
title: "new hdd shared but won't mount"
date: 2009-06-16
forum: Networking &amp; Wireless
---

### Post by curracruisers on 2009-06-16
Hi Guys, I have a fat32 hdd which is used in Windows as well as Ubuntu 9.04 64bit as data storage.

It is mounted by "fstab" at boot,
It is mounted in "/home/trevor/maxtor", 
It mounts and read/writes ok locally,
In Nautilus "properties/share" it says it is shared,
It can be seen from network browser on local machine, 
It can be seen by another computer on the network, 
Other folders in the "/home/trevor" folder share and network access ok
](*,)but here's the problem
It won't mount on either system when viewed via the network.
"Failed to mount" error

I have just tried another drive that is fat32 and it does the same!! So the problem relates to Fat32 it seems!!

The error only happens to this vfat drive! I don't want it to be ext3 as I need it in Windows. The drive shared/mounted fine in Ubuntu 8.10. Any Ideas?

---

### Post by curracruisers on 2009-07-13
Bump: Has anyone been able to duplicate this problem or is it all working for for everyone but me?

---

