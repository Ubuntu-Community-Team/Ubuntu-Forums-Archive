---
title: "Can't mount DVDs"
date: 2009-07-29
forum: Multimedia Software
---

### Post by elcisitiak on 2009-07-29
I can't mount DVDs using Jaunty. 

All the tutorials I've seen direct the userd to install the libdvdread4 and libdvdcss2 packages, both of which I already have. 

I can burn DVDs (but not DVD-DLs, although my drive is compatible with them), but I can't play anything back. The drive simply refuses to mount. 

I can mount CDs without a problem. 

I've tried several DVDs, but nothing works, though all work on different DVD players. Even the DVDs that I burn from this machine won't play back, although they play just fine in a proper DVD player. 

The DVDs I'm currently working with are commercial, and play just fine on another DVD player.

rel@Set:~$ sudo mount -t udf -o force /dev/cdrom /mnt
mount: no medium found on /dev/sr0

Nothing changes in dmesg when the disk is inserted. 

The drive makes a sound, I can tell it's physically trying to read the disk, but the system reports no media found. I need to back these up before traveling this weekend, so please help me!

---

