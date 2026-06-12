---
title: "complete ext4 FS borkage after today's updates"
date: 2010-09-28
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by recluce on 2010-09-28
I updated my Maverick test install today as usual (aptitude safe-upgrade) and the process completed without any error messages. After finishing some work, I rebooted the machine, only to be dumped to the dreaded TTY prompt after the plymouth graphical boot screen.

Usually, this just means some X11 problem, so I tried to check on xorg.conf - which wasn't there. Also, the fs turned out to be read-only! I rebooted again (to go to recovery mode and was greeted by this (had to write this down, so not complete):

```

Kernel Panic - not syncing VFS: unable to mount root fs on unknown-block (0,0)

PID: 1, comm: swapper Not tainted 2.6.35-22-generic #33- Ubuntu

```

I booted into Lucid after that and ran e2fsck on the partition. There are LOTS of unresolvable problems, like double assigned nodes belonging to the kernel and init.

At this point, I would usually presume a hardware problem, as the corruption is massive. However, all tests come back without problems, the SMART status of the drive is good, there are no I/O errors, all other partitions of the drive are fine. No remapped sectors, nothing. "Torture tests" writing to the drive for several hours turned up nothing.

My test setup: Ubuntu 10.10 x64 on a secondary SATA drive (AHCI), booted from a dedicated GRUB partition on my primary SSD. File system is ext4.

Any ideas, anybody?

---

### Post by gradinaruvasile on 2010-09-28
I had the same problem with 9.10. And i could not mount that ext4 partition anymore - no amount of googling, fscking helped...
Since then i use only ext3 for system partitions.
Tis probably doesnt help you solve it. But there is a chance that the partition is lost.

---

