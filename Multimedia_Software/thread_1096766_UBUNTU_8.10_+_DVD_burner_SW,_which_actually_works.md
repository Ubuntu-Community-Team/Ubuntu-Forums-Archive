---
title: "UBUNTU 8.10 + DVD burner SW, which actually works?"
date: 2009-03-15
forum: Multimedia Software
---

### Post by John.St on 2009-03-15
I have tried a few DVD burners, e.g. k3b, xfburn and brasero to burn a 31 GB backup.

Each of them told me either to insert a 31 GB DVD!!!! or "capacity exceeded by 23 GB". Start resp. Burn is greyed out.

Or am I completely wrong in assuming that it is possible to insert more than one DVD before I have to throw the drive away?

Any ideas?

---

### Post by damis648 on 2009-03-15
All of the software works fine, but DVD's can only hold 4.7Gb per layer. If you wanted to burn to sequential DVD's, I don't think there's even Windows software for that, let alone Ubuntu. Just split the backup into sections of 4.7Gb (or 9Gb for dual layer DVD's), then burn each DVD.

---

### Post by John.St on 2009-03-15
That's a possibility, damis648, but if I can split a tar.gz file and burn 7 DVDs then decent SW can do the same. We wrote that kind of SW 30 years ago so we could back the huge 36 MB disks up on 5.2 MB Falcons.

---

### Post by John.St on 2009-12-08
This has been solved with brasero in ub 9.10

---

### Post by ed bear on 2012-04-05
I swear by good old DRIVE IMAGE, whose incarnation as "Norton Image Centre 5.6" can handle ext2 partitions.  In fact, that's why I keep my main partition as ext2 rather than ext3!

I can boot from a DOS 6.22 floppy to back up or restore even if the drive being restored to is virgin or hosed, and save the file in pieces of any size I pick.

Brasero does my burning, with almost no learning curve.

Restrictions:
- no ext3 support (gparted can back up ext3 partitions but you have to have Ubuntu running and CAN'T back up a mounted drive)
- you have to save the backup to a FAT partition, so while you can use large partitions, the maximum piece size is 2GB.
- DOS won't support SATA or USB drives, or write to CD or DVD; I save to a DOS partition and then use Ubuntu to copy the pieces to wherever I want to put them, or burn them to CD or DVD.
- putting DOS drivers into the boot sequence of your DOS boot floppy WILL let you write to any DOS-supported device such as a Zip drive. (Bet you won't find any that are 31GB, though!)
- the DOS MSCDEX drivers WILL let you RESTORE from CD/DVD directly.

ED BEAR
:cool:

---

### Post by mörgæs on 2012-04-05
Old thread, closed.

---

