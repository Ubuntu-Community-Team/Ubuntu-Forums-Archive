---
title: "How to burn an UDF image?"
date: 2010-02-12
forum: Multimedia Software
---

### Post by rdeleonp on 2010-02-12
Ubuntu 9.10 here.

I'm trying to preserve my DVD collection, so I want to use DVD backups instead of the originals. I did the following:

```
$ dd if=/dev/sr0 of=FightClub.iso bs=2048 conv=notrunc

$ ls -l FightClub.iso
-rw-r--r-- 1 rdl rdl 8039299072 2010-02-10 09:55 FightClub.iso

$ file FightClub.iso
FightClub.iso: UDF filesystem data (version 1.5) 'FIGHT_CLUB                     '
```I can read the file just fine using Totem, but how do I burn this type of file directly to 8.5GB media?

I tried brasero and k3b, but, after burning, I cannot read the disks on my PC or DVD player...

---

### Post by enzomatrix on 2010-02-25
Just to clear things up.
Did you use the command
```
dd if=/dev/sr0 of=FightClub.iso bs=2048 conv=notrunc

```
on an original DVD? I mean, a movie DVD with zone protection.
If this is the case, that is the problem. You cannot copy a protected DVD without removing the protection. BTW, removing the protection to make a backup is illegal in some countries, even if you want to use the backup and keep the original safe.
To do this, you should use some program like K9copy that "unprotects" the DVD.

---

### Post by Gryphen on 2010-06-19
All you have to do to copy a dvd is install libdvdcss2 then use k3b to copy the dvd. look at the link in my sig,

---

