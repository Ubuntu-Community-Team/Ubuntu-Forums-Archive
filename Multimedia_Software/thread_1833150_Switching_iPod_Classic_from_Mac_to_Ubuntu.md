---
title: "Switching iPod Classic from Mac to Ubuntu"
date: 2011-08-25
forum: Multimedia Software
---

### Post by ritchiew on 2011-08-25
I had some issues getting my 80GB iPod Classic to even connect to my new Ubuntu laptop. Angry "Mount Error" anytime I would connect. I couldn't find anything in the forums that were very helpful, so I'll just throw down what I learned.

Since I had been syncing from my Mac, my iMac had reformatted the iPod drive to some Apple standard HTFS, I believe. This gives Apple the extra opportunity to lock down the device, so when you plug it into an Ubuntu Machine, you get an angry Mount Error.

There are lots of hacky ways around it. There is also the simple way around it:

1) Plug the iPod into the Mac.

2) Use Disk Utility to format the drive as FAT32 *** THIS DELETES ALL MUSIC ON THE IPOD****

3) Open iTunes. It will restore the firmware, but say NO to anything it asks you. Don't Sync. Don't reformat. When the iPod just says "Connected" again, eject it.

4) Stick it in the Ubuntu computer. Now instead of "Mount Error" popping up, I got "Media Device Detected. Open in Banshee?"

5) Life if good.

Now, as I say, this method deletes everything on the ipod. But if you're switching from Mac to Ubuntu and have moved over all the mp3s already, this is by far the easiest thing to do.

---

