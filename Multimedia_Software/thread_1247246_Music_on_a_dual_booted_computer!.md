---
title: "Music on a dual booted computer!"
date: 2009-08-22
forum: Multimedia Software
---

### Post by schalich11 on 2009-08-22
I recently got a new laptop and i dual booted it with windows and ubuntu. I have a bunch of music i want to move onto my laptop and i would love to be able to listen to the music on both operating systems. Is having a copy of each song for both operating systems the only way to do this? or is there a way to have my music on my harddrive only once and access it from both operating system? Thanks!

---

### Post by aysiu on 2009-08-22
Actually, that's probably not the way to go.

If you're not using a Wubi dual-boot, you can store it on the Windows partition and have Ubuntu automount the Windows partition and use the Windows music folder as the Ubuntu music folder.

Or you can do the reverse (but you'll need a special plugin to get Windows to read the Ubuntu partition).

Or you can create a separate shared partition that's FAT32 and can be read from and written to both Windows and Ubuntu natively.

---

