---
title: "k3b failed to burn CD image"
date: 2007-06-19
forum: Multimedia &amp; Video
---

### Post by xjgnsdof on 2007-06-19
I use Feisty 7.04 and have had no problems burning DVDs and CDs. I tried to burn a CD image in k3b but got the following message:

System
-----------------------
K3b Version: 1.0

KDE Version: 3.5.6
QT Version:  3.3.7
Kernel:      2.6.20-16-generic
Devices
-----------------------
HL-DT-ST DVD-RW GWA-4082N CC15 (/dev/hdc, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite]

Used versions
-----------------------
cdrecord: 1.1.2

cdrecord
-----------------------
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.2
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 1 = CD-ROM
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identification : 'DVD-RW GWA-4082N'
Revision       : 'CC15'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009 (CD-R)
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x001A (DVD+RW) 
Profile: 0x001B (DVD+R) 
Profile: 0x002B (DVD+R/DL) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x000A (CD-RW) 
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1053696 = 1029 KB
Drive DMA Speed: 9628 kB/s 54x CD 6x DVD
FIFO size      : 12582912 = 12288 KB
/usr/bin/wodim: No such file or directory. Cannot open FILE '/home/user/Desktop/Downloads/GT2/A/GT2 - A.part01.rar_FILES/D:\RIPPED MUSIC\GT2_A.BIN'.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/hdc speed=24 -dao driveropts=burnfree cuefile=/home/user/Desktop/Downloads/GT2/A/GT2 - A.part01.rar_FILES/GT2.cue -eject

---

### Post by xjgnsdof on 2007-06-19
up

---

### Post by dabl on 2007-06-19
I have a problem with K3b in Feisty also.  I posted on the Kubuntu forum a week ago and everyone else claimed "no problem here".  :(

Have you tried gnomebaker or brasero?  It would be nice to confirm that your hardware and basic Linux configuration are all correct, by burning a CD with one of the other packages.  If that works, then you know it's JUST K3b, and not a hardware thing.  Guess I need to try my own advice!  :)

---

### Post by xjgnsdof on 2007-06-21
Gnomebaker also doesn't work. I've burned images to CDs before; I wonder what's going on.

---

### Post by dabl on 2007-06-21
Sounds like the CD ROM drive is not configured quite right, either in /etc/fstab or elsewhere in your system.

In looking at the K3b output, that line "scsidev: '/dev/hdc'" looks a bit odd -- scsi devices are normally designated "sdxx" not "hdxx".  You might want to google on recent (feisty) changes to device designations, wrt PATA/ATAPI devices versus SCSI devices.  You might need to change the designation of that drive in fstab.  :)

---

### Post by paulg on 2007-06-21
Are you using a cue file? Check out this line in the error log:
```
/home/user/Desktop/Downloads/GT2/A/GT2 - A.part01.rar_FILES/D:\RIPPED MUSIC\GT2_A.BIN
```

Edit the cue file in your favourite text editor and change "D:\RIPPED MUSIC\GT2_A.BIN" to "GT2_A.BIN" save in the same folder as the bin file and try again. It is looking for the bin file in a path that doesn't exist, or make sense.

~pAul.

---

### Post by xjgnsdof on 2007-06-21
I can't believe I didn't figure that out. I'm at work, but I'll let you know what happens when I get home to my cache of blank CD-Rs.

---

### Post by xjgnsdof on 2007-06-21
paulg, when I renamed that section of the cue file in a text editor, k3b told me "seems not to be a usable image."

dabi, that fstab file is read only

Still won't burn CD images.

---

### Post by stchman on 2007-06-21
Download a .iso image and try to burn that.  Try Damn Small Linux.  It is about 50MB download.

---

### Post by xjgnsdof on 2007-06-22
I converted the bin and cue files to iso, and k3b burned it perfectly. Do I really have to do this every time I want to burn a CD image?

---

### Post by xjgnsdof on 2007-07-03
So, has anyone figured out a way to burn CD images without converting the files to ISO first?

---

### Post by dabl on 2007-07-03
> **elgilicious said:**
> 
Do I really have to do this every time I want to burn a CD image?

No, that's crazy talk!  ;)

I think your file system table (fstab) is wrong.  You are correct that it is read-only for the user.  But the Super User can modify it when required.

```
gksu gedit /etc/fstab
``` will bring it up for editing, but BE CAREFUL -- better (a) back it up first, and (b) know what you're trying to do, before you start editing.

Like I said before, your CD/DVD drive should appear in fstab as a "/media/scdx" device, I would think.  I'm posting my fstab, and showing you what a CD/DVD drive that works correctly looks like -- it is the third line from the bottom that begins "/media/scd0 ":

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
<device> /media/cdrom0 auto nouser,noauto,atime,rw,nodev,noexec,nosuid 0 0
# /dev/sdb2
UUID=84445218-c1c0-41fc-9616-2c92a5a348d5 / reiserfs nouser,notail,atime,auto,rw,dev,exec,suid 0 1
# /dev/sdb3
UUID=788345ee-79d6-4298-bca3-e5b6f02f6a68 /home reiserfs nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
# /dev/sda1
UUID=2db802ca-39f5-41f3-bcff-f23e9139a24e /media/sda1 reiserfs nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
# /dev/sda3
UUID=4157eb7a-7a16-4ce7-8774-06f247c61dc6 /media/sda3 reiserfs nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
# /dev/sdb1
UUID=8000EEFB00EEF6D6 /media/sdb1 ntfs defaults,nls=utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
# /dev/sdc1
UUID=5c75276d-48e9-4705-a19c-94210edf8c2a /media/sdc1 reiserfs nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
# /dev/sdc3
UUID=9b7658da-59e1-4b2b-a4b9-fa3ee11b68cf /media/sdc3 reiserfs nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
# /dev/sdc2
UUID=f9c52547-7ede-4e39-b35c-ce764f290de6 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto, 0 0
/dev/fd0 /media/floppy0 auto user,atime,noauto,rw,dev,exec,suid 0 0
/dev/sdd1 /media/mickey auto nouser,atime,noauto,rw,nodev,noexec,nosuid 0 0
```

---

### Post by xjgnsdof on 2007-07-04
Thanks. The following is my fstab file:

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/hda2 :
UUID=b6f2394b-680f-4351-beda-e15b1c6c234b / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hda4 :
UUID=8fba0704-45a5-4f85-9999-94bd2357c87c /home ext3 defaults 0 2
# Entry for /dev/hda1 :
UUID=046026B86026AFFA /media/hda1 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/hda3 :
UUID=2608156f-046e-4903-bb4b-8ffee2893b21 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0

---

### Post by xjgnsdof on 2007-07-19
Here is the error log that appears when I try to burn a cue file in k3b.

System
-----------------------
K3b Version: 1.0

KDE Version: 3.5.6
QT Version:  3.3.7
Kernel:      2.6.20-16-386
Devices
-----------------------
HL-DT-ST DVD-RW GWA-4082N CC15 (/dev/hdc, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite]

Used versions
-----------------------
cdrecord: 2.1.1a03

cdrecord
-----------------------
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.2
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
wodim: No such file or directory. Cannot open FILE '/home/emones/Games/GT2/AD/D:\RIPPED MUSIC\GT2.BIN'.
TOC Type: 1 = CD-ROM
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identification : 'DVD-RW GWA-4082N'
Revision       : 'CC15'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009 (CD-R)
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x001A (DVD+RW) 
Profile: 0x001B (DVD+R) 
Profile: 0x002B (DVD+R/DL) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x000A (CD-RW) 
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1053696 = 1029 KB
Drive DMA Speed: 9614 kB/s 54x CD 6x DVD
FIFO size      : 12582912 = 12288 KB

cdrecord command:
-----------------------
/usr/bin/cdrecord -v gracetime=2 dev=/dev/hdc speed=10 -dao driveropts=burnfree cuefile=/home/emones/Games/GT2/AD/GT2.cue -eject

---

### Post by mark541 on 2007-07-27
I'd been running Ubuntu 6.06 (Dapper) for just under a year. During that time, I've burned dozens of CDRs and DVDs with no problem. 

I recently upgraded to 7.04 (Feisty) and now it's terrible. I just used 18 CDRs while burning 10 CDs (8 coasters, 10 good CDs). 

My hardware didn't change, so it seems likely it's something in Feisty. I tried both wodim (the fork of cdrecord) and cdrdao and had problems with both. I've tried slowing down the speed, forcing TAO, or DAO or RAW, but nothing seems to work.

I've got my error listings in bug #114122 if you want to see the output from K3b with failures using both wodim and cdrdao.

---

### Post by shibboleth on 2007-09-14
when I attempt to copy a CD with 7.04, I receive a VFS error. "the folder contents could not be displayed."  I am using the Serpentine Player.  Please advise.

---

