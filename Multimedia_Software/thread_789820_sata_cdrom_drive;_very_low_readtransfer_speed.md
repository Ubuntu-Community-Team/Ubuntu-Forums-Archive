---
title: "sata cdrom drive; very low read/transfer speed"
date: 2008-05-10
forum: Multimedia Software
---

### Post by angryhomer17 on 2008-05-10
My sata cdrom drive (Samsung SH-S183L) is very slow at reading discs. This is causing problems when copying discs to the hard drive or when burning.

For example, it took me 86 seconds to copy ~750 MB worth of data from my sata cdrom to my sata hard disk in krusader. That is ~8.72 MB/s.

It appears that cp is somewhat faster. For the same files it took 50 seconds to copy 750 MB. That's 58% better or ~15 MB/s.

From my reading it appears that either:

a. sata cdrom drives do not support dma
     or
b. sata cdrom drives already use dma and it cannot be turned on or off

Here is what hdparm shows for speeds for my cdrom and hard drives:

cdrom
```
~$ sudo hdparm -Tt /dev/scd0 

/dev/scd0:
 Timing cached reads:   6242 MB in  2.00 seconds = 3123.30 MB/sec
 Timing buffered disk reads:   20 MB in  3.08 seconds =   6.49 MB/sec

```

main hard drive
```
$ sudo hdparm -Tt /dev/sda

/dev/sda1:
 Timing cached reads:   7390 MB in  2.00 seconds = 3698.19 MB/sec
 Timing buffered disk reads:  188 MB in  3.00 seconds =  62.64 MB/sec

```

secondary hard drive
```
$ sudo hdparm -Tt /dev/sdb1 

/dev/sdb1:
 Timing cached reads:   7682 MB in  2.00 seconds = 3844.89 MB/sec
 Timing buffered disk reads:  238 MB in  3.01 seconds =  79.20 MB/sec

```

As you can see both of the sata hard drives have reasonable buffered disk reads while the cdrom is a measly 6.49 MB/s. And that is an improvement from the ~2.50 MB/s I was getting before doing this:

[http://ubuntuforums.org/showthread.php?t=678153&highlight=sata+cdrom+slow#9](http://ubuntuforums.org/showthread.php?t=678153&highlight=sata+cdrom+slow#9)

Here is what happens when I try to set dma:

```
~$ hdparm -d1 /dev/scd0 

/dev/scd0:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device


```
and this is hdparm for the drive
```

$ hdparm /dev/scd0 

/dev/scd0:
 IO_support    =  0 (default) 
16-bit)
 HDIO_GET_UNMASKINTR failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_KEEPSETTINGS failed: Inappropriate ioctl for device
 readonly      =  0 (off)
 readahead     = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

```

Burning a disc with brasero gives read speed of about 5.5x or ~7200 KiB/s. With k3b I am getting a copy speed of about 430 MB/min or 7.16 MB/s

Just creating a cd image for a standard 12 track audio cd takes just over 6 minutes.

This is way too long to wait on a machine more than capable of faster speeds. It seems like 8.04 still has some problems to be worked out. 

Any suggestions?

---

### Post by angryhomer17 on 2008-05-13
anybody? dvd rips taking over 30 mins is no fun.

---

### Post by mc4man on 2008-05-13
> My sata cdrom drive (Samsung SH-S183L) is very slow at reading discs
It may have 'riplock' which will impact ripping speeds particularly commercial dvds
ck. here - [http://club.cdfreaks.com/f105/sh-s183l-slow-ripping-cds-222620/](http://club.cdfreaks.com/f105/sh-s183l-slow-ripping-cds-222620/)
there's probably a review on main site somewhere
there may be a firmware fix here [http://www.rpc1.org/](http://www.rpc1.org/) - site is down for a bit - if a firmware is available usually needs to be done in windows

---

### Post by angryhomer17 on 2008-05-13
Thanks. This looks like it will prolly help. Hopefully, I can get it to run under wine. Will try out once I can get the frimware, after the server issue is fixed.

---

### Post by mc4man on 2008-05-13
_If_ there is a firmware do some reading and or post in that sites forum, borking a firmware flash can kill your drive. I would be hesitant to try in linux (wine or otherwise ) without specific instructions

slightly ot but same idea - all of my dvd drives can be set to booktype dvd+r, +rw to dvd-rom. I can't set the drive for this in linux (not that i'm aware of), so I set them in xp and when burning in linux the booktype is set as intended.

---

### Post by angryhomer17 on 2008-05-21
Well rpc1's site is back up finally. I looked around for the SH-S183L firmware for a bit, but I am having trouble finding it. Perhaps you could help me out on that.

If I do decide to go ahead with the flash, do you think there would be a problem if I did the flash through Windows in virtualbox? I really don't feel like doing a native install on another partition. That and I don't have the option to use another computer, because I don't have any extra with sata on them.

So that being said, maybe I should look at adding an additional drive. What are some suggestions that are under $50 and rip well? Thanks.

---

### Post by angryhomer17 on 2008-05-27
Well I tried flashing the firmware, but it hasn't worked so far. 

I've tried using the patch from codeguys with the following:

The firmware patch:
[http://codeguys.rpc1.org/firmwares_samsung.html](http://codeguys.rpc1.org/firmwares_samsung.html)

The flashers:
MediaCodeSpeedEdit
[http://ala42.cdfreaks.com/MCSE/](http://ala42.cdfreaks.com/MCSE/)

Can't find my drive in the list.
-----------------
SFDNWIN - Samsung Flasher
[http://codeguys.rpc1.org/firmwares_samsung.html](http://codeguys.rpc1.org/firmwares_samsung.html)

Errors out saying the firmware is not for my drive
----------------
Patch Utility for Samsung MTK based DVD Writers v3.0.1
[http://club.cdfreaks.com/f105/patch-utility-samsung-mtk-based-dvd-writers-v3-0-1-new-242508/](http://club.cdfreaks.com/f105/patch-utility-samsung-mtk-based-dvd-writers-v3-0-1-new-242508/)

This isn't a flasher I found out. It appears to just change the firmware and allows you to save the file. Didn't see an option to remove riplock.

Not sure what to do now.

---

### Post by bigtoedsloth on 2009-04-06
I know this is a very old thread, but ...

Is there are solution to this low speed problem (other than buying another drive)?  I have exactly the same drive with exactly the same frustrating issue.

---

### Post by Sefianix on 2009-05-07
bump

me too.

---

### Post by angryhomer17 on 2009-05-10
I guess I've gotten used to how slow my drive is. It sucks, but the thing sometimes goes all foobar on me....might be time to get a new drive (bluray?). If I have a chance I'll do some testing in Jaunty and see if there is any new things to kill this riplock bull. Hooray for evil monkeys!

---

### Post by chartguy on 2012-09-20
I have a similar issue. I'm using Brasero Disc Burner under the latest version of Ubuntu (64-bit AMD, 12.04 LTS). The CD-ROM reads at a miserable 658 KiB/s (3.8x), while it will write a copy at 5138 KiB/s (29.8x).

In other words, it takes longer to read the original than it does to burn seven copies.

It's a basic ASUS CD/DVD drive. I'll try to find a model number.

---

### Post by wildmanne39 on 2012-09-20
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

