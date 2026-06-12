---
title: "ImgBurn (via wine) verification problem"
date: 2008-09-10
forum: Multimedia Software
---

### Post by misha680 on 2008-09-10
I need to use ImgBurn because it is the only program that successfully booktypes on my TSSTCorp CDDVDW SN-S082H (Samsung) drive. Burn goes fine but verification I start to see problems (I've attached a screenshot). I am using Windows NT 4.0 as my wine version and the ASPI I/O driver under ImgBurn. Wine is latest Hardy deb from WineHQ. Same burn works and verifies fine on Windows. Any help would be appreciated.

Thank you
Misha

p.s. basically it pretty much looks like it stops verifying the disc at 49%.

---

### Post by mc4man on 2008-09-10
Looks like the verify is hanging right at the end of layer0, if the disk plays back fine I wouldn't worry too much. I always use SPTI as the io, have you tried that?

Did you notice any burn slowdown or buffer emptying around that point (48 - 51 %

Side note - If you see verbatim dl's at a decent price get them instead. (usually can be had for around $2 ea.

---

### Post by misha680 on 2008-09-10
> **mc4man said:**
> Looks like the verify is hanging right at the end of layer0, if the disk plays back fine I wouldn't worry too much. I always use SPTI as the io, have you tried that?

Did you notice any burn slowdown or buffer emptying around that point (48 - 51 %

Side note - If you see verbatim dl's at a decent price get them instead. (usually can be had for around $2 ea.

Thanks. I tried SPTI but I couldn't booktype (cannot access memory region). Actually weird quirk is if I do autodetect drives in WineCfg then SPTI will detect the drive (and ASPI) but neither will let me booktype with same message.

If I _don't_ autodetect drives, SPTI doesn't work, but ASPI works fine and _will_ let me booktype (and in fact the discs seem to have the correct booktype as opposed to, say, one I tried burning with dvd+rw-tools and k3b).

I will probably do a diff of some kind to check the image just in case. I guess dd and diff is good enough, there's not a specialized tool for this is there?

Thank you
Misha

---

### Post by mc4man on 2008-09-10
The booktype setting is done on the drive itself so as long as your using Imgburn you shouldn't have to set it again. I usually set my drives in Xp **once** and they always come out as such (dvd-rom for +R's and dl's. (ie., I never go to that setting again
Most drives that can burn dl's by default are set to booktype as dvd-rom anyway.

I never use the linux burning apps but i guess they're not respecting the drives booktype setting (from what you've observed

I've noticed the latest wine vers. >1.0 have been 'losing' one of my drives from boot to boot - gotten in the habit now of running winecfg before burning.

Imgburn can confirm the booktype of your burned disks in read mode

---

### Post by misha680 on 2008-09-10
> **mc4man said:**
> The booktype setting is done on the drive itself so as long as your using Imgburn you shouldn't have to set it again. I usually set my drives in Xp **once** and they always come out as such (dvd-rom for +R's and dl's. (ie., I never go to that setting again
Most drives that can burn dl's by default are set to booktype as dvd-rom anyway.

I never use the linux burning apps but i guess they're not respecting the drives booktype setting (from what you've observed

I've noticed the latest wine vers. >1.0 have been 'losing' one of my drives from boot to boot - gotten in the habit now of running winecfg before burning.

Imgburn can confirm the booktype of your burned disks in read mode

Thank you. Samsungs reset booktype on each open of the drive (or at least mine does and the cdfreaks forums say this as well).

Misha

---

### Post by mc4man on 2008-09-10
> Samsungs reset booktype on each open of the drive 
> If I _don't_ autodetect drives, SPTI doesn't work, but ASPI works fine and _will_ let me booktype

This is very good info to know, learn something every day.


edit: in the case of drives that can have the booktype set permanently a cd/dvd creator burn does use the setting on the drive (brasero wasn't interested in burning the image

> Physical Format Information (Last Recorded):
Disc ID: CMC MAG-M01-00
Book Type: DVD-ROM
Part Version: 1

---

### Post by misha680 on 2008-09-11
> **mc4man said:**
> This is very good info to know, learn something every day.


edit: in the case of drives that can have the booktype set permanently a cd/dvd creator burn does use the setting on the drive (brasero wasn't interested in burning the image

So ran into a caveat doing dd on drives per 
```
dd if=/dev/hdc bs=2048 count=n | md5sum
```
all the ones I did on ImgBurn via wine are only 3.7 GB, whereas the one I burned on Windows is ~8. Guess I can't booktype my drive on Linux :(

Misha

---

### Post by mglukhovsky on 2008-09-11
I have the exact same problem. I use ImgBurn to burn DVDs because it generates IBG graphs which I use with DVDInfoPro to ensure a steady burn.

I've been burning DVDs for a while, and when it comes to DVD video nothing ensures a steady burn like examining these graphs.

I tried several tests to see if I could replicate the issue. Burning DVDs using ImgBurn works, but verifying it results in an error at a certain point in the disc. Burning DVDs using Brasero and then verifying them using ImgBurn also results in an error.

Here's the sticking point: A burnt DVD in Brasero verifies perfectly on ImgBurn in Windows Vista.

Clearly there is an issue with Wine. Any thoughts?

---

### Post by mglukhovsky on 2008-09-20
Problem fixed in today's release of Wine (1.15).

---

