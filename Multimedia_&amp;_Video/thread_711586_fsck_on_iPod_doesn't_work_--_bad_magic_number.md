---
title: "fsck on iPod doesn't work -- bad magic number"
date: 2008-02-29
forum: Multimedia &amp; Video
---

### Post by clararaubertas on 2008-02-29
So I have Rockbox on my first-gen iPod Nano, which worked great for a while on one Ubuntu installation.
I didn't use the iPod for a while, and now I have a brand new Ubuntu install and the iPod seems to be having some filesystem issues:

-- Ubuntu doesn't automount the pod, but I have no problem manually mounting it
-- I can read the files on it and copy them to my desktop's hard drive
-- The iPod charges via USB and plays music
-- I can remove files from the ipod
-- BUT, when I try to copy new music to the iPod,  it says "writing [filename]: Input/output error" and creates empty files on the ipod

-- fsck does the following:
```
clara@boffin:~$ fsck -a /dev/sdf2 
fsck 1.40.2 (12-Jul-2007)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
FSINFO sector has bad magic number(s):
  Offset 0: 0x40604252 != expected 0x41615252
  Offset 484: 0x60017232 != expected 0x61417272
  Offset 510: 0xaa11 != expected 0xaa55
  Auto-correcting it.
Got 327680 bytes instead of 1907996 at 16384

```

and all the behavior is the same before/after fsck. I'm stumped -- is the drive just busted (my instinct is no, since I can read from it fine)? Do I need some kind of fsck alternative/different fsck options?

thanks in advance for any insight!

---

