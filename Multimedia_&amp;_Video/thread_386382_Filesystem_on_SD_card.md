---
title: "Filesystem on SD card"
date: 2007-03-16
forum: Multimedia &amp; Video
---

### Post by andrei.kouznetsov on 2007-03-16
Hi, guys!

Does anybody know what filesystem should be on an SD card (Secure Digital) that a "regular" player could understand it?

I've corrupted original file system. After I made a new one with

mkfs -t vfat /dev/mmcblk0p1

my player stopped playing. I tried 

mkfs.msdos -F 16 /dev/mmcblk0p1

and the result was the same :(

Finally, I put the card into my digital camera and it formatted it properly. So, I'm curious, what the correct FS is, because it is not alway very convenient to use a digital camera to format a media :)

---

### Post by andrei.kouznetsov on 2007-03-17
If you know the way to get the information for the file system that works, then I can get it and print. Maybe it will help

---

