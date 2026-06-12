---
title: "Mythbuntu 14.04 Will Not Mount XFS"
date: 2014-11-28
forum: Mythbuntu
---

### Post by jlp_engineer on 2014-11-28
I have a fresh install of Mythbuntu 14.04 on an old 1U server.  I have the system booting successfully to a RAID 5 volume formatted with EXT4, and I have a single large disk formatted to XFS where all Myth content is saved.  I can mount the disk using "sudo mount /dev/sdb1 /mnt/disk", but I am unable to stick this into fstab and get it to mount during boot.  I have used the UUID and /dev/sdb1 for fstab and nothing works.  I am only able to load it manually after boot.  I have looked and made sure that xfsprogs is loaded.  I loaded this same disk in fstab under Mythbuntu 12.04, but when I started fresh (formatted the boot array, but left the XFS volume untouched) it didn't work.  I have checked and the mount point has full permissions, root:root with full wrx permissions.

What am I missing?

---

### Post by uteck on 2014-11-28
What line are you using /etc/fstab?  Seems like you might be missing an option or it is in the wrong order.
should look like this:
/dev/sdb1   /mnt/disk   xfs   defaults 0 2

---

