---
title: "DVD Won't Write - Now Stopped Reading too"
date: 2011-05-30
forum: Multimedia Software
---

### Post by KutWrite on 2011-05-30
My laptop internal DVD drive won't write:

Problem writing iso image to DVD-RW or DVD-R

I have:
Ubuntu 11.04 with current updates as of 5/25/11
Toshiba A665 S2100x laptop (i7 processor w/6gB)
Internal DVD Device is a Matshita BD-CMB UJ141EL
DVD is a Maxell DVD-RW disk
Ext. Drive is TSSTcorp CD/DVDW SH-S162L (USB connection)

Blank DVD is not seen in internal drive when inserted, but K3B sees disk.
DVD with movie is seen by K3B but does not show in "places".
In Places/Computer "CD Drive" for internal and 
"CD/DVD Drive" for external drive. 
External drive sees blank & asks what to run with it.
I created Ubuntu recovery disks fine when installing 10.10 and later, 11.04. So int.
drive should be OK physically.

K3B Error when attempting to write the iso:

i Writing DVD-RW in DAO mode.
i Using Wodim 1.1.11 - Copyright...
i Starting SAO writing at 2x speed...
x cdrecord has no permission to open the device.
x You may use K3bsetup to solve this problem.  

Same DVD wrote fine using K3B in the external DVD drive. The disk is read in the ext. drive, but is seen as an empty drive when put into internal DVD drive.

Int. drive itself is seen as existing but empty by K3B and Ubuntu Disk Utility.

When written DVD-RW is put into ext. drive, it's seen fine, and menu created on iso image via DeVeDe also appears and operates normally.

Mounted "movie.iso" shows up on desktop - mounted by K3B I think.  Int. disk drive does not show up when disk is inserted.

Changed permissions for internal DVD drive per recommendations in K3B settings menu.

Error reports from K3B:

Try 1:

Devices
-----------------------
MATSHITA BD-CMB UJ141EL 1.00 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, BD-ROM, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW, BD-ROM] [SAO, TAO, RAW, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite] [%7]
TSSTcorp CD/DVDW SH-S162L TS04 (/dev/sr1, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump] [%7]

System
-----------------------
K3b Version: 2.0.2
KDE Version: 4.6.2 (4.6.2)
QT Version:  4.7.2
Kernel:      2.6.38-8-generic-pae

Used versions
-----------------------
cdrecord: 1.1.11

cdrecord
-----------------------
/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
scsidev: '/dev/sr0'
devname: '/dev/sr0'
scsibus: -2 target: -2 lun: -2
Error trying to open /dev/sr0 exclusively (Device or resource busy)... retrying in 1 second.
=== last message repeated 4 times. ===
Error trying to open /dev/sr0 exclusively (Device or resource busy)... giving up.
/usr/bin/wodim: Device or resource busy. 
Cannot open SCSI driver!
For possible targets try 'wodim --devices' or 'wodim -scanbus'.
For possible transport specifiers try 'wodim dev=help'.
For IDE/ATAPI devices configuration, see the file README.ATAPI.setup from
the wodim documentation.
TOC Type: 1 = CD-ROM

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/sr0 speed=2 -sao driveropts=burnfree -data -tsize=1166437s -


Try 2:

Devices
-----------------------
MATSHITA BD-CMB UJ141EL 1.00 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, BD-ROM, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW, BD-ROM] [SAO, TAO, RAW, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite] [%7]
TSSTcorp CD/DVDW SH-S162L TS04 (/dev/sr1, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump] [%7]

System
-----------------------
K3b Version: 2.0.2
KDE Version: 4.6.2 (4.6.2)
QT Version:  4.7.2
Kernel:      2.6.38-8-generic-pae

- - - - - - - - - -

Will try using Windows 7 with drive later.   I have a dual boot machine, but didn't want to lose this post.

Any thoughts of what to try w/in Ubuntu?  Somehow I think it's some setting somewhere that got knocked awry during the last update.  BTW the drive does whir and the seek head flips around a bit after inserting the disk, so it knows something's there.

Thanks!

OK... it's 5/31 and I rebooted in Win7. The DVD drive worked fine. Read the DVD and what's on it; played in DVD Player.

OK, rebooted in Ubuntu and now the system sees the drive!  I'll try erasing the -RW.
Well, it erased.
Now, I'm re-burning the iso image using K3B.

So... I guess i fixed it.  Not sure how, but my bet is using the "Settings' feature of K3B and accepting its suggested changes to permissions did the trick.

Hope this helps someone!

---

