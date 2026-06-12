---
title: "Coling Mythbuntu disk with dd doesn't make a PERFECT copy"
date: 2013-10-14
forum: Mythbuntu
---

### Post by yonkiman on 2013-10-14
[Post subject should be "***Cloning ***Mythbuntu disk with dd doesn't make a PERFECT copy" but it looks like I can't edit the subject...]

To back up my mythbuntu system, I periodically clone the entire disk to another disk using dd.  That's the simplest, fastest, and most reliable way I know to make a complete copy of my working system.  After the cloning I can boot from either disk as they are identical for all practical purposes.

The command I use (it's a 46.57GB partition with unallocated space after it) is:
sudo dd if=/dev/sde of=/dev/sdf bs=2048k count=23000

This has worked may times, with several different hard disks (my primary 80GB Intel SSD and several much larger Seagate hard drives).

A few weeks ago I did the usual backup with the intention to upgrade Myth from 0.26 to 0.27 on the hard drive, then clone it back to the SSD once I had it working.  The upgrade went fine, but when I cloned it back to the SSD, the SSD booted into Ubuntu fine, but when it tried to launch MythFrontEnd, it started with the "welcome" screen (choose your country, etc.), as if I was installing myth for the first time.

When I boot off the hard disk it works normally.

I don't understand how dd could copy the OS perfectly, but somehow be missing something that makes myth think this is a new config?

I'm always booting from the same physical SATA cable (/dev/sde), so it's not that the system thinks the drive location has changed.
The drives (since they have the same UUID) are never mounted at the same time.  They're only ever connected at the same time when I do the cloning (from inside a PartedMagic USB-drive boot).

It doesn't seem possible!  What am I missing?

---

### Post by yonkiman on 2013-10-14
OK, I just tried it again, this time first doing a [secure erase]("https://ata.wiki.kernel.org/index.php/ATA_Secure_Erase") on the SSD.  I also increased the dd block count to 25000 from 23000.  

It worked!  I don't know why or which change did it (23000 worked fine in the past...), but maybe this info might help someone someday...

---

