---
title: "Slow CIFS/SMB Traversal with Ubuntu, Fast with Arch Linux"
date: 2010-01-18
forum: Networking &amp; Wireless
---

### Post by orphaze on 2010-01-18
I've got cifs mounted windows share on two linux systems here, an older system running Arch Linux with kernel 2.6.21, and my brand new Ubuntu system with kernel 2.6.31-17.

If I do "ls -R" on the cifs mounted share (which is on a Windows 7 machine) on the older Arch linux system, it takes about 1/4 of a second to list some 3000 files in 50 or so folders. If I do the same on my Ubuntu system, it takes 6-7 seconds to read all the files out. These times are repeatable and consistent. Both systems mount the share using the same command. (mount -t cifs -o username=X,password=X //system/share /mountpoint)

This delay is causing a program I use to playback media files (the MythVideo plugin of MythTV) to take 6-7 seconds to load the full directory tree each time I open it, something I do quite frequently.

Are there any tips/tricks out there to speed up the traversal of cifs mounted shares? If not, what would you recommend I would to do try and figure out what the cause of this delay is?

Everything else on both systems works perfectly, and file transfers from the Windows machine to linux machines go pretty much the exact same speed. This makes me think the network is not to blame, though I'm open to any possibilities.

Anything you could recommend would be very much appreciated, thanks.

---

