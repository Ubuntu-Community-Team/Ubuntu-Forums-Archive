---
title: "Weird Ipod behavior!"
date: 2009-09-13
forum: Multimedia Software
---

### Post by Benic on 2009-09-13
I have a Ipod nano (2Gb) that I was able to fully use in earlier versions of Ubuntu. Now, with 9.04, there are some strange things going on. 

I can mount the ipod manually. There is no icon on the desktop and I can't mount/umount it with nautilus. I can browse files in nautilus and with gtkpod (no editing possible), but not with amarok or rythmplayer (which I used to be able to previously). 

The strangest thing happens when I try fdisk -l. Every time I unplug/plug the ipod, it goes from /dev/sdb1 to sdc1, sdd1, sde1 and so on. So I can't change the settings in fstab and automount it.

I don't have this kind of problem with other devices such as usb key or usd hard drive. 

Why does the ipod keeps changing location when I do fdisk -l? How can I make it automount again?

Thanks!

---

### Post by Benic on 2010-04-27
Well, upgrading to 9.10 with a clean install solved the problem. Still I don't know how to solve it without doing such a radical operation...

---

