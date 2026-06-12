---
title: "Why are all my music files owned by root?"
date: 2008-07-28
forum: Multimedia Software
---

### Post by nothingspecial on 2008-07-28
Should they be and will this have an effect on loading my ipod?

---

### Post by silkstone on 2008-07-28
Where are these files? In your home folder or on an external (FAT32 or NTFS) drive?

If they are in your home folder they should be owned by you. If on an external drive, ownership and permissions are not recognised by Windows filesystems, so they may show as being owned by root. If you copy them to your home folder, you should become the owner.

---

### Post by nothingspecial on 2008-07-28
Thanks for the reply
They`re are on an external hard drive, and I (a lazy Ubuntu only user) never bothered to reformat the drive `cause it just worked. The drive has never been plugged into a windows machine. 
Can I do a sudo chmodwhateveritis *mp3?

---

### Post by nothingspecial on 2008-07-28
Also the file is too big to go on the pcs internal drive.

---

### Post by silkstone on 2008-07-28
They should be OK where they are - no need to reformat unless you really want to. Both FAT32 and NTFS work with Linux and Windows. If you copy any of the files to your home folder on the (Linux) drive, the permissions should be changed anyway. You should also be able to copy them to another drive or player and they will work. In the case of FAT32 or NTFS drives, 'root' ownership effectively means 'no ownership'!

P.S. For the same reason, you can't 'chmod' to change permissions on Windows filesystems, because ownerships are not supported.

---

### Post by nothingspecial on 2008-07-28
That has answered my question!
Thanks again.:)

---

### Post by RuleMaker on 2008-07-28
You can chmod the directory that contains your music (or the whole partition or even a drive).
Do this:
```
chmod a+x+w+r /media/<the name you assigned for the mount point
```
This will give all users rights to execute, read and write on that drive, including your mp3 files.

---

