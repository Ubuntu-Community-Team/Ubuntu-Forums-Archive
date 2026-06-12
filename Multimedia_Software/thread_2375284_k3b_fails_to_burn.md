---
title: "k3b fails to burn"
date: 2017-10-23
forum: Multimedia Software
---

### Post by aparolin on 2017-10-23
first off; thanx for responses...

my setup;
using linux on a chromebox,
hp printer works, monitor works, sound works, keyboard works, usb drives work
attached a simple cd/dvd burner,
downloaded and installed k3b software,
ran setup, checked and authorized device... did not check burning group.
setup found external programs;  cdrdao, cdrecord, growisofs.
tried to burn photos and this error dump followed;
also, mkisofs crashed
         probably a buffer underrun occurred 
         use lower burn speed  (i used 10x)

[what am i missing???]
Devices
-----------------------
Slimtype DVD A  DS8A5SH XA15 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump] [%7]

K3b::IsoImager
-----------------------
mkisofs print size result: 165399 (338737152 bytes)

System
-----------------------
K3b Version: 2.0.3
KDE Version: 4.14.16
QT Version:  4.8.7
Kernel:      4.8.17-galliumos

Used versions
-----------------------
mkisofs: 1.1.11
cdrecord: 1.1.11

cdrecord
-----------------------
scsidev: '/dev/sr0'
devname: '/dev/sr0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.11
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 3 = CD-ROM XA mode 2
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'Slimtype'
Identification : 'DVD A  DS8A5SH  '
Revision       : 'XA15'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009 (CD-R)
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0012 (DVD-RAM) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE FORCESPEED 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 946176 = 924 KB
FIFO size      : 12582912 = 12288 KB
resid: 60
resid: 24
Speed set to 1765 KB/s
Track 01: data   323 MB        
Total size:      371 MB (36:45.34) = 165401 sectors
Lout start:      371 MB (36:47/26) = 165401 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 7
  Is not unrestricted
  Is not erasable
  ATIP start of lead in:  -11538 (97:28/12)
  ATIP start of lead out: 359849 (79:59/74)
Disk type:    Long strategy type (Cyanine, AZO or similar)
Manuf. index: 7
Manufacturer: GIGASTORAGE CORPORATION
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 194448
Forcespeed is OFF.
Starting to write CD/DVD at speed  10.0 in real TAO mode for multi session.
Last chance to quit, starting real write in    2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... resid: 24
resid: 60
=== last message repeated 2 times. ===
input buffer ready.
Performing OPC...
resid: 60
Starting new track at sector: 0
Track 01:    0 of  323 MB written.
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 00 00 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 21 02 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x21 Qual 0x02 (invalid address for write) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 63488
cmd finished after 0.010s timeout 40s
/usr/bin/wodim: The current problem looks like a buffer underrun.
/usr/bin/wodim: It looks like 'driveropts=burnfree' does not work for this drive.
/usr/bin/wodim: Please report.
/usr/bin/wodim: Make sure that you are root, enable DMA and check your HW/OS set up.
write track data: error after 0 bytes
Writing  time:   15.833s
Average write speed 291.1x.
Fixating...
Fixating time:   24.934s
/usr/bin/wodim: fifo had 192 puts and 2 gets.
/usr/bin/wodim: fifo was 0 times empty and 1 times full, min fill was 99%.
BURN-Free was never needed.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/sr0 speed=10 -tao driveropts=burnfree -multi -xa -tsize=165399s -

mkisofs
-----------------------
165399
I: -input-charset not specified, using utf-8 (detected in locale settings)
Using UTAHNATURALBRIDGESBEARSE000.JPG;1 for  2017utah-co/utahnaturalbridgesbearsears4.JPG (utahnaturalbridgesbearsears3.JPG)
Using UTAHNATURALBRIDGESBEARSE001.JPG;1 for  2017utah-co/utahnaturalbridgesbearsears3.JPG (utahnaturalbridgesbearsears2.JPG)
Using UTAHNATURALBRIDGESBEARSE002.JPG;1 for  2017utah-co/utahnaturalbridgesbearsears2.JPG (utahnaturalbridgesbearsears.JPG)
Using UTAHCANYONLANDSNEEDLES2000.JPG;1 for  2017utah-co/utahcanyonlandsneedles2.jpg (utahcanyonlandsneedles2.JPG)
Using UTAHCANYONLANDSGRANDVIEW000.JPG;1 for  2017utah-co/utahcanyonlandsgrandviewpoint2.JPG (utahcanyonlandsgrandviewpoint.JPG)
Using COGUNNISON5000.JPG;1 for  2017utah-co/cogunnison5.JPG (cogunnison5.jpg)
  0.31% done, estimate finish Mon Oct 23 12:14:05 2017
  0.61% done, estimate finish Mon Oct 23 12:14:05 2017
  0.91% done, estimate finish Mon Oct 23 12:14:05 2017
  1.21% done, estimate finish Mon Oct 23 12:14:05 2017
  1.52% done, estimate finish Mon Oct 23 12:14:05 2017
  1.82% done, estimate finish Mon Oct 23 12:14:05 2017
  2.12% done, estimate finish Mon Oct 23 12:14:05 2017
  2.43% done, estimate finish Mon Oct 23 12:14:05 2017
  2.73% done, estimate finish Mon Oct 23 12:14:05 2017
  3.03% done, estimate finish Mon Oct 23 12:14:05 2017
  3.33% done, estimate finish Mon Oct 23 12:14:05 2017
  3.63% done, estimate finish Mon Oct 23 12:18:40 2017

mkisofs calculate size command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -print-size -quiet -volid 2017utah-co -volset  -appid K3B THE CD KREATOR (C) 1998-2010 SEBASTIAN TRUEG AND MICHAL MALEK -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-aparolin/k3boN6192.tmp -rational-rock -hide-list /tmp/kde-aparolin/k3bHV6192.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-aparolin/k3bbc6192.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 3 -path-list /tmp/kde-aparolin/k3brx6192.tmp

mkisofs command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -volid 2017utah-co -volset  -appid K3B THE CD KREATOR (C) 1998-2010 SEBASTIAN TRUEG AND MICHAL MALEK -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-aparolin/k3bGz6192.tmp -rational-rock -hide-list /tmp/kde-aparolin/k3bdu6192.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-aparolin/k3bUV6192.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 3 -path-list /tmp/kde-aparolin/k3bIf6192.tmp



i figure i need to go into terminal and add a command; but i dont have the foggiest??????

---

### Post by seeker5528 on 2017-10-23
> **aparolin said:**
> first off; thanx for responses...


Starting new track at sector: 0
Track 01:    0 of  323 MB written.
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 00 00 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 21 02 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x21 Qual 0x02 (invalid address for write) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 63488
cmd finished after 0.010s timeout 40s
/usr/bin/wodim: The current problem looks like a buffer underrun.
/usr/bin/wodim: It looks like 'driveropts=burnfree' does not work for this drive.
/usr/bin/wodim: Please report.
/usr/bin/wodim: Make sure that you are root, enable DMA and check your HW/OS set up.
write track data: error after 0 bytes


Whenever I see input/ouput errors I am suspicious of it being a hardware issue, but since it looks like it fail right away and indicates that it looks like burnfree is not supported by the drive, you can try burning without that enabled.

There is a checkbox to enable/disable burnfree in the k3b GUI under 'settings --> advanced'.

If it still fails I would starting looking at the hardware side of things, if it is a USB drive try different cable, different USB port. In particular if it is a USB port that has seen a fair amount of devices being plugged in/unplugged the port may be a little worn.

If it is internal in a desktop machine and you have another SATA port to plug in to, you can try a diffferent port, different cable.

Not the most common case, but I have seen with desktops and laptops plenty of times where just unplugging/replugging cables, removing/reinserting drives gets them to work again. 

I'm not so good on the software side of the troubleshooting of burning issues, so maybe someone else will chime in with some additional ideas there.

---

### Post by aparolin on 2017-10-27
dis-enabled burnfree as suggested;
burn failed with similar output.....
completely removed k3b and installed xfburn.
xfburn works perfectly!!!!!!!!!
not as flashy, but it works......in my case
thanx to seeker5528 for the suggestion
good luck to all
case solved, case closed

---

### Post by jpberes on 2017-10-29
Dear,
A while ago when I was using Kubuntu and other distros with KDE, I regularly had some problems burning CD's/DVD's with K3b,
It was adviced to use and install xfburn .. since then I'm using on whatever distro xfburn and this without any problems and/or trouble.
Maybe an idea to install xfburn and give it a try ?
Regards,
JP

---

