---
title: "Feisty - CD Works Fine same drive DVD drive Autoplay but no mount? Eh?"
date: 2007-04-20
forum: Multimedia &amp; Video
---

### Post by ToucanSam on 2007-04-20
I have been running Feisty from Herd 4. I have all the updates installed.
I have installed the restricted packages, libdvdcss, totem-xine, vlc, and anything else I can think of to get this thing to work.

CDs mount on the desktop on insert as they should, I can browse them through nautilus.

DVDs do not mount on the desktop, and I can not browse them through nautilus. The strange thing is that when I put them, they play movies.

from fstab:    
 >  /dev/scd0        /media/cdrom0   udf,iso9660 user,noauto     0       0 

When I put in a dvd it now mounts as CD-ROM 1, when i try to browse it:

>  mount: special device /dev/scd0 does not exist 

So following the trail, i look in dev. There is no scd0 so.... which do I use in my fstab. 
Update:

So I run > dmesg | grep -i dvd 

and get:

> [    7.368338] hdc: VOM-12E48X, ATAPI CD/DVD-ROM drive
[    8.050977] hdc: ATAPI 47X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)


I change my fstab to read:

> /dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


And still no luck

Any ideas?

Thanks,
Bkkkkawwwk

---

### Post by Wight_Rhino on 2007-04-22
I'm seeing a lot of "mount" threads started, with few answers and I was wondering if they are related to this bug;

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/94119](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/94119)

It would be a mistake to assume that they all are, but it may be worth looking into.

---

### Post by ToucanSam on 2007-04-23
Thanks for the reply, I had heard about the problems with 2.6.20 kernel relating to mount as well. Just dont think I have run into anything that wasn't able to be fixed by a little poking around. I think I downloaded an update to 2.6.20-15 the other day. I guess it still isnt fixed. I also have a copy of Feisty64 that things seem to be working ok on. I'll give it another go tonight.

---

