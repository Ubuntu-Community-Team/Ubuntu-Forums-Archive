---
title: "Blu-Ray fails on Hardy"
date: 2008-05-30
forum: Multimedia Software
---

### Post by browneej on 2008-05-30
I have installed 8.04 multiple times and ways.  My SONY Blu-Ray IDE drive fails to install every time--the live cd fails to load and the alternate cd fails integrity checks.  The cds are good.  I had to use a DVD-ROM to install.  This has only happened recently, in the switch from 7.10 to Hardy.

Once installed, I attempted to switch back to the Blu-Ray.  While the drive is fully accessible and I can copy files off it (and write to DVD's and CD's on it), neither VLC, Totem, MPlayer, or Xine will play movies.  The first three crash, and Xine insists I don't have the proper permissions (though it will show the first second of a movie first) and boots me out.  I have verified cdrom group membership etc.

I have also tried changing settings in the bios for the drive from auto to CHS, Large, and LBA, with no joy.

Anyone have any ideas?

---

### Post by mc4man on 2008-05-30
I don't have a blu-ray drive so this is just a thought. With a disk in the drive and mounted maybe try a different 'approach'
use this as the base command
```
export DVDCSS_METHOD=title && vlc dvd://
``` (normally would access a disc at dev/dvd) and try adding on either the mountpoint or device. Ex.
```
export DVDCSS_METHOD=title && vlc dvd:///media/cdrom0
``` (or cdrom1 - whatever the drive is )
Maybe also try from root
```
export DVDCSS_METHOD=title && sudo vlc dvd:///media/cdrom0
```
Before trying I'd delete any folder(s) assoiated with title to be 'played' from .dvdcss (hidden in home dir.)
You could substitute totem, xine, ect. for vlc in above if wanted

---

### Post by browneej on 2008-06-04
Thanks for the reply.

I did something different.  Based on the busybox & initramfs string [http://ubuntuforums.org/showthread.php?t=765195](http://ubuntuforums.org/showthread.php?t=765195), I loaded the live cd with:

--all_generic_ide floppy=off irqpoll

The live cd loaded for the first time since I downloaded 8.04, yeah!  I was able to install, and once I booted off the hd, I was able to play dvd's off the blu-ray.  I still can't mount or read blu-ray disc's, so I'll have to look for hd dump and the other software necessary.

For the record, the alternate cd still failed even with the kernel options above.

---

### Post by mc4man on 2008-06-04
Good to hear about dvds
for blueray you need udf 2.5, i know there is a recent thread but can't find it.
here's one though
[http://ubuntuforums.org/showthread.php?t=718744](http://ubuntuforums.org/showthread.php?t=718744)

---

