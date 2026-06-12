---
title: "howto force erase CD-RW"
date: 2007-03-18
forum: Multimedia &amp; Video
---

### Post by tallman9 on 2007-03-18
Once ago I cloned a very scratched cd using k3b and wrote it on a CD-RW just to test it...it didn't work and also when I try to blank this CD-RW it just refuses...I've tried almost all the gui apps and even directly from CLI, but no luck so far.
I had such an issue over a year ago in windoze and I managed it using Alcohol(a proprietary program).
It's been over half a year since I've switched completely to linux and I don't wish to use windoze(also can't afford it) and this Alcohol program.

Is there a way to force blank the CD-RW under linux?
or will I have to install wine and emulate alcohol?(I don't really wish to do it)
perhaps, just throw away the CD-RW? =)

here is what k3b tells me after I try to blank it:
> System
-----------------------
K3b Version: 0.12.17

KDE Version: 3.5.5
QT Version:  3.3.6
Kernel:      2.6.17-10-386
Devices
-----------------------
ASUS CB-5216A 1.12 (/dev/hdd, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD+R; DVD+R DL] [DVD-ROM; DVD+R Double Layer; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R]

Used versions
-----------------------
cdrecord: 2.1.1a03

cdrecord command:
-----------------------
/usr/bin/X11/cdrecord.mmap -v gracetime=2 dev=/dev/hdd speed=10 -tao driveropts=burnfree -eject blank=all -force 

cdrecord
-----------------------
/usr/bin/X11/cdrecord: Warning: Running on Linux-2.6.17-10-386

/usr/bin/X11/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/X11/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdd'
devname: '/dev/hdd'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
/usr/bin/X11/cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c 1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
Cdrecord-Clone 2.01.01a03 (i686-pc-linux-gnu) Copyright (C) 1995-2005 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.
TOC Type: 1 = CD-ROM
Using libscg version 'debian-0.8debian2'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'ASUS    '
Identifikation : 'CB-5216A        '
Revision       : '1.12'
Device seems to be: Generic mmc2 DVD-ROM.
Current: 0x000A
Profile: 0x000A (current)
Profile: 0x0009 
Profile: 0x0008 
Profile: 0x0002 
Profile: 0x0010 
Profile: 0x002B 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
/usr/bin/X11/cdrecord: Success. read disk info: scsi sendcmd: no error
CDB:  51 00 00 00 00 00 00 00 04 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 02 00 00 00 00 0A 00 00 00 00 3A 01 00 00
Sense Key: 0x2 Not Ready, Segment 0
Sense Code: 0x3A Qual 0x01 (medium not present - tray closed) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 4
cmd finished after 0.000s timeout 240s
/usr/bin/X11/cdrecord: Cannot get disk type.
/usr/bin/X11/cdrecord: Success. set cd speed: scsi sendcmd: no error
CDB:  BB 00 03 72 06 EA 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 02 00 00 00 00 0A 00 00 00 00 3A 00 00 00
Sense Key: 0x2 Not Ready, Segment 0
Sense Code: 0x3A Qual 0x00 (medium not present) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.000s timeout 40s
/usr/bin/X11/cdrecord: Cannot set speed/dummy.
/usr/bin/X11/cdrecord: Success. test unit ready: scsi sendcmd: no error
CDB:  00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Drive buf size : 1365760 = 1333 KB
Current Secsize: 0
Waiting for drive to calm down.
Starting to write CD/DVD at speed 10 in real force BLANK mode for single session.
Last chance to quit, starting real write in 3 seconds.
Sense Bytes: 70 00 02 00 00 00 00 0A 00 00 00 00 3A 01 00 00
Sense Key: 0x2 Not Ready, Segment 0
Sense Code: 0x3A Qual 0x01 (medium not present - tray closed) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.000s timeout 40s
   2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Starting to write CD/DVD at speed 10 in real force BLANK mode for single session.
No chance to quit anymore. Operation starts.
Performing OPC...
Blanking entire disk
/usr/bin/X11/cdrecord: Success. blank unit: scsi sendcmd: no error
CDB:  A1 00 00 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 02 00 00 00 00 0A 00 00 00 00 3A 01 00 00
Sense Key: 0x2 Not Ready, Segment 0
Sense Code: 0x3A Qual 0x01 (medium not present - tray closed) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.000s timeout 9600s
/usr/bin/X11/cdrecord: Success. test unit ready: scsi sendcmd: no error
CDB:  00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 02 00 00 00 00 0A 00 00 00 00 3A 01 00 00
Sense Key: 0x2 Not Ready, Segment 0
Sense Code: 0x3A Qual 0x01 (medium not present - tray closed) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.000s timeout 40s
/usr/bin/X11/cdrecord: Success. test unit ready: scsi sendcmd: no error
CDB:  00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 02 00 00 00 00 0A 00 00 00 00 3A 01 00 00
Sense Key: 0x2 Not Ready, Segment 0
Sense Code: 0x3A Qual 0x01 (medium not present - tray closed) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.000s timeout 40s
/usr/bin/X11/cdrecord: Success. blank unit: scsi sendcmd: no error
CDB:  A1 00 00 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 02 00 00 00 00 0A 00 00 00 00 3A 01 00 00
Sense Key: 0x2 Not Ready, Segment 0
Sense Code: 0x3A Qual 0x01 (medium not present - tray closed) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.000s timeout 9600s
/usr/bin/X11/cdrecord: Cannot blank disk, aborting.


---

### Post by kerry_s on 2007-03-18
It looks like a permission thing, you should fix that in your settings. You can just start k3b as root> kdesu k3b <or if using in gnome> gksu k3b
Also i see alot of "medium no present", you sure your disk is good?

---

### Post by tallman9 on 2007-03-19
The disc is ok 100%
simply the image of the disc I burned on it was cloned from a very scratched one.
It's not a permissoin thing for sure, I'm not a newbie in linux/ubuntu and of course I've done that > start k3b as root> kdesu k3b <or if using in gnome> gksu k3b just after I installed k3b.
Also, I have the same CD-RW's that I use on daily basis and I got no problem with them(I can blank them and burn anything I want on them).

---

### Post by kerry_s on 2007-03-19
Then maybe that cd rw has just reached the end of it's life. I know they can be written to only so many times, of course they do on occasion just go bad, i've seen on more then 1 occasion were the disk was just cheap, placed in the sun, placed near a magnet,....

---

### Post by tallman9 on 2007-03-19
> **kerry_s said:**
> Then maybe that cd rw has just reached the end of it's life. I know they can be written to only so many times, of course they do on occasion just go bad, i've seen on more then 1 occasion were the disk was just cheap, placed in the sun, placed near a magnet,....
sorry, but I think it's really not the case...
anybody else got different ideas?

---

### Post by krugger on 2007-03-20
Try

sudo cdrecord blank=all -immed dev=/dev/cdrw

should completely blank you cdrw.

Expect it to take 30 minutes, as it is not fast deleting just the headers, but zeroing the whole cdrw.

---

### Post by tallman9 on 2007-03-20
I'll try that, thanks.

here is what it shows me:
> tallman[~]> sudo cdrecord blank=all -immed dev=/dev/cdrw
Password:
Cdrecord-Clone 2.01.01a03 (i686-pc-linux-gnu) Copyright (C) 1995-2005 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.17-10-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/cdrw'
devname: '/dev/cdrw'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Using libscg version 'debian-0.8debian2'.
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c	1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'ASUS    '
Identifikation : 'CB-5216A        '
Revision       : '1.12'
Device seems to be: Generic mmc2 DVD-ROM.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
cdrecord: CD/DVD-Recorder not ready.
tallman[~]> sudo cdrecord blank=all -immed dev=/dev/cdrom
Cdrecord-Clone 2.01.01a03 (i686-pc-linux-gnu) Copyright (C) 1995-2005 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.17-10-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/cdrom'
devname: '/dev/cdrom'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Using libscg version 'debian-0.8debian2'.
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c	1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'ASUS    '
Identifikation : 'CB-5216A        '
Revision       : '1.12'
Device seems to be: Generic mmc2 DVD-ROM.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
cdrecord: CD/DVD-Recorder not ready.

still not working :(

---

### Post by bigboy_pdb on 2007-05-21
Hello tallman9,

Did you try to unmount the device for the CD-RW drive before blanking the CD?

To do this type the following in a terminal:
umount /dev/cdrw

If that doesn't unmount the CD-RW then type 'mount' to see which devices are mounted. The cd drive should be mounted to a folder named something like '/media/cdrom0' and it should be of type 'iso9660'. If there are a lot of devices that have been mounted you can try 'mount | grep iso9660' or 'mount | grep cd' so that only the lines containing 'iso9660' or 'cd' are displayed (respectively).

After this you should be able to type the following into the command line to erase the disk:
cdrecord blank=fast dev=/dev/cdrw

where '/dev/cdrw' should be the device for the CD-RW drive.

If you prefer to use a tool which has a GUI, it should work as well (once the CD-RW is unmounted).

Also, you don't need to be root/super user to do this. Furthermore, this doesn't erase the whole CD (to do that replace 'fast' with 'all'), and for more information on cdrecord you can use 'man cdrecord' in a terminal.

I hope this is helpful,
Dave

---

