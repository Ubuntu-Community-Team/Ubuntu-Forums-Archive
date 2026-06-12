---
title: "iPod Shuffle 2nd Gen Reformatted Incorrectly - Won't Show"
date: 2010-04-21
forum: Multimedia Software
---

### Post by acconrad on 2010-04-21
Hello,

I'm running 9.10 and here's how I got myself into this mess:

-Rhythmbox wouldn't show my ipod shuffle, so I moved to Amarok and Exaile, but both wouldn't let me move files to my iPod
-Gtkpod would allow me to, but the ipod shuffle said it has a Read-Only File System. I read to fix that, you can reformat it to be FAT32

In the error of my dumb ways, I simply right-clicked and hit "Format..." as a FAT filesystem without any regard for what would happen if that didn't work. It didn't -- it said there was not enough room for a FAT filesystem formatting, and now the file system is totally FUBARed. 

It won't mount, nothing is there (well, it won't recognize any type of partition, but it only has 250MB of its approx 1GB of space free), and when I try to create even an msdos partition in GParted for /dev/sdb (which I can at least get to that), GParted terminates early and cannot do anything.

So currently I have a corrupted iPod Shuffle 2nd Gen that all I care about is working again. I don't care that I lost the music, I just want to nuke it, put a file system on it that Gtkpod will recognize and allow me to throw music on it.

Thanks!

---

### Post by acconrad on 2010-04-25
bump?

---

### Post by tgalati4 on 2010-04-26
Find iTunes and perform a restore.  There's also a separate shuffle restore tool, but you will have to search for it.  Otherwise Apple will fix it for $99.

You are beyond reformat, as you wiped the boot code.

---

