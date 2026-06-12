---
title: "Dvd Drive doesn't appear. VLC crashes Mythbuntu"
date: 2011-07-14
forum: Mythbuntu
---

### Post by Jake.Debord on 2011-07-14
Two problems!

New to Mythbuntu... I have a problem with my dvd drive not mounting. It doesn't show up on file system. It appears on desktop when a dvd is inserted, but that is the only way to access it. No folder on file system named /dev/dvd like I would assume and this is also the default path to dvd in VLC so I assume this SHOULD be where it should appear. Also, when I use VLC to try to play the dvd I point it to the place where it does show up /dev/media/%nameofdisk% It starts to play and menu works fine. But, when I decide to move the window around to position it differently on my screen it completely crashs Mythbuntu back to the login screen. When I try to play the dvd through Mythtv optical disks it plays, but it looks horrible, its got green lines through the video etc.

Your help is greatly appreciated!!!!!

---

### Post by nickrout on 2011-07-15
things are not mounted in /dev, devices appear in /dev and are mounted elsewhere in the filesystem.

You dvd is probably being mounted under ~/.gvfs. The mount command will tell you though, and the device that is being mounted.

---

### Post by Jake.Debord on 2011-07-17
Well in Ubuntu its visible with out without anything in the tray so I assume mythbuntu doesnt support this dvd rom

---

### Post by nickrout on 2011-07-18
> **Jake.Debord said:**
> Well in Ubuntu its visible with out without anything in the tray so I assume mythbuntu doesnt support this dvd rom

ubuntu and mythbuntu have the same kernel so if it works in ubuntu ot will work in mythbuntu.

with a dvd mounted tell us the result of the following commands:

```
mount
ls ~/.gvfs
```

---

