---
title: "Easy software RAID in Ubuntu?"
date: 2009-01-31
forum: Networking &amp; Wireless
---

### Post by avahi on 2009-01-31
Hey new user here :)

In OS X, I like how it's really easy to make a software-based RAID setup. All you have to do is open Disk Utility.

Does Ubuntu offer the same functionality?

Can I make a setup without erasing the original drive?

[img]http://img98.imageshack.us/img98/8025/picture1xi6.png[/img]

---

### Post by kidders on 2009-02-02
Isn't OS X great! The trouble with Linux is that there are just too many ways something like this could be achieved, so people can be slow to agree on one. For example, one obvious problem with the Apple way is the assumption that a RAID array's component devices have to be disks.

> **avahi said:**
> Does Ubuntu offer the same functionality?Not that I would trust. Configuring RAID manually is by far the best approach.

> **avahi said:**
> Can I make a setup without erasing the original drive?No.

I know this is exactly what you *don't* want to hear. That said, creating a new RAID device isn't really all that complicated anyway. In broad strokes ...[LIST]
[*]Use a disk partitioner to set aside the disk space necessary for your array ... unless of course you want to build it out of entire hard disks.
[*]Run **mdadm --create**. You now have a RAID array on which you can store one or more filesystems.
[*]Run **mkfs** to write a filesystem onto the array.
[*]If you like, add a line to **/etc/fstab** to have the array mounted automatically on boot.
[/LIST]

I hope that helps.

---

