---
title: "NFS issues on Ubuntu-Mac network share"
date: 2009-01-06
forum: Networking &amp; Wireless
---

### Post by NewYork12436 on 2009-01-06
I have an NFS share setup on a MacPro (running Leopard 10.5.5) mounted on my Ubuntu box (running Dapper), and it works great in the short term for pulling files off the Mac for processing in Ubuntu (mostly for HD film work). However, in the long term I've noticed odd and fatal problems cropping up on both machines since I instituted the share.

If the share is left mounted for some time (longer than a few hours), Ubuntu gets very sluggish and then will crash altogether. Likewise, just today I had a file system catalog become corrupted on the Mac's RAID! (DiskWarrior came to the rescue).

Does anyone have experience with NFS and this kind of setup? Are there any better alternatives? SMB is much slower, and I don't think AoE is an option in Mac-land.

The boxes are just connected on a gigabit LAN, and the share is simply mounted with "mount -t nfs ....", nothing fancy (although getting the Mac to allow the share took some doing).

Please help! Thanks!

---

