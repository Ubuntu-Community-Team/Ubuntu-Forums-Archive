---
title: "Why won't CDs play more easily? (cdrom0 vs hda?)"
date: 2006-11-17
forum: Multimedia &amp; Video
---

### Post by wilberfan on 2006-11-17
I've been playing with both gnome and KDE, and I seem to have trouble consistenly playing music CDs under both...

Could it have anything to do with this:

My DVD and CD drive seem to get mounted to /media/cdrom0 and /media/cdrom1, respectively.   But many of the players can't 'find' the disc when specified like that.   When I look in my fstab file, those two devices are called 'hda' and 'hdb'...

When I, for example, tell Beep Media Player to look for a disk at 'hda' it DOES find it, and LOOKS like it's playing it (counters are going)--but there is no sound.

I just tried playing a CD with  KsCD--and it, too, wouldn't recognize the CD until I told it to look at 'hda'.   But it won't play at all...   It seems to be READING the name of the disk and the track names, but the counters won't move and there is no sound...

Is there something fundamental going on here--or are these separate issues?    Is there another way I should be configuring my media players?

---

### Post by TheWizzard on 2006-11-18
> **wilberfan said:**
> I've been playing with both gnome and KDE, and I seem to have trouble consistenly playing music CDs under both...

Could it have anything to do with this:

My DVD and CD drive seem to get mounted to /media/cdrom0 and /media/cdrom1, respectively.   But many of the players can't 'find' the disc when specified like that.   When I look in my fstab file, those two devices are called 'hda' and 'hdb'...

When I, for example, tell Beep Media Player to look for a disk at 'hda' it DOES find it, and LOOKS like it's playing it (counters are going)--but there is no sound.

I just tried playing a CD with  KsCD--and it, too, wouldn't recognize the CD until I told it to look at 'hda'.   But it won't play at all...   It seems to be READING the name of the disk and the track names, but the counters won't move and there is no sound...

Is there something fundamental going on here--or are these separate issues?    Is there another way I should be configuring my media players?

hda and hdb are supposed to be your hard disks, not your cd and dvd drives. 

if you insert a cd, an icon should appear on your desktop. 
you should be able to right-click the icon and select play cd.

---

### Post by temcat on 2006-11-19
> **TheWizzard said:**
> hda and hdb are supposed to be your hard disks, not your cd and dvd drives. 


This is not the case if you have SATA hard drives and IDE CD drives.

---

### Post by wilberfan on 2006-11-19
> **temcat said:**
> This is not the case if you have SATA hard drives and IDE CD drives.

*Exactly! * I DO have two SATA HDs in that box.  A CD (or DVD) will mount and be displayed on the desktop--but I think there's perhaps only ONE program that will play them properly (and I can't remember which one that is right at the moment...)

---

### Post by Shatrat on 2006-11-19
I had this problem as well and I think it comes from some missing gstreamer plugins and such.
Check out this thread, [http://ubuntuforums.org/showthread.php?p=1622845](http://ubuntuforums.org/showthread.php?p=1622845)

I installed goobox as well and it installed some gstreamer dependencies that made everything else work.  If I remembered exactly which dependencies were updated I would let you know, but it was a while ago.

---

### Post by wilberfan on 2006-11-19
Thanks for the tip--but it didn't help...  Does 'goobox' end up as "CD Player" in the menu?  Cuz that crashes when I try and play a CD with it...

---

