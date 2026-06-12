---
title: "Burning problem on 10.10"
date: 2010-09-27
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by vmonkey on 2010-09-27
Hi all,
I am experiencing a really weird problem. I updated to beta version of Ubuntu 10.10 and now I can't burn nor CDs nor DVDs in any program (tried K3B and Brasero).
As far as I can say I didn't use any burning application while having Lucid.
To manage this problem I tried to boot Slax from liveUSB and there it worked. Therefore, it is clear that the bug must be in Ubuntu and not in hardware.
I own laptop HP 620.
And here I attach log from K3B:

> Devices
-----------------------
hp CDDVDW TS-L633N 0300 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump] [%7]

K3b::IsoImager
-----------------------
mkisofs print size result: 2133900 (4370227200 bytes)

System
-----------------------
K3b Version: 2.0.1
KDE Version: 4.5.1 (KDE 4.5.1)
QT Version:  4.7.0
Kernel:      2.6.35-22-generic

Used versions
-----------------------
mkisofs: 1.1.10
cdrecord: 1.1.10

cdrecord
-----------------------
scsidev: '/dev/sr0'
devname: '/dev/sr0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.10
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 1 = CD-ROM
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'hp      '
Identification : 'CDDVDW TS-L633N '
Revision       : '0300'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0011 (DVD-R sequential recording)
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0012 (DVD-RAM) 
Profile: 0x0011 (DVD-R sequential recording) (current)
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) 
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) 
Using generic SCSI-3/mmc DVD-R(W) driver (mmc_mdvd).
Driver flags   : SWABAUDIO BURNFREE 
Supported modes: PACKET SAO
Drive buf size : 1406976 = 1374 KB
FIFO size      : 12582912 = 12288 KB
Speed set to 11080 KB/s
Track 01: data  4167 MB        
Total size:     4786 MB (474:12.00) = 2133900 sectors
Lout start:     4786 MB (474:14/00) = 2133900 sectors
Current Secsize: 2048
HINT: use dvd+rw-mediainfo from dvd+rw-tools for information extraction.
Blocks total: 2298496 Blocks current: 2298496 Blocks remaining: 164596
Starting to write CD/DVD at speed   8.0 in real SAO mode for single session.
Last chance to quit, starting real write in    2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Errno: 5 (Input/output error), send opc scsi sendcmd: no error
CDB:  54 01 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 72 0B 00 00 00 00 00 0E 09 0C 00 00 00 03 00 00
Sense Key: 0x0 No Additional Sense, Segment 11
Sense Code: 0x00 Qual 0x03 (setmark detected) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 3.395s timeout 200s
/usr/bin/wodim: OPC failed.
/usr/bin/wodim: faio_wait_on_buffer for writer timed out.
Errno: 0 (Success), prevent/allow medium removal scsi sendcmd: no error
CDB:  1E 00 00 00 00 00
status: 0x28 (BUSY)
cmd finished after 200.003s timeout 200s
Writing  time:  803.469s
/usr/bin/wodim: fifo had 192 puts and 0 gets.
/usr/bin/wodim: fifo was 0 times empty and 0 times full, min fill was 100%.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/sr0 speed=8 -sao driveropts=burnfree -data -tsize=2133900s -

mkisofs
-----------------------
2133900
I: -input-charset not specified, using utf-8 (detected in locale settings)
  0.02% done, estimate finish Sun Sep 26 00:04:28 2010
  0.05% done, estimate finish Sat Sep 25 22:21:38 2010
  0.07% done, estimate finish Sat Sep 25 21:46:40 2010
  0.09% done, estimate finish Sat Sep 25 21:28:38 2010
  0.12% done, estimate finish Sat Sep 25 21:18:10 2010
  0.14% done, estimate finish Sat Sep 25 21:11:09 2010
  0.16% done, estimate finish Sat Sep 25 21:06:08 2010
  0.19% done, estimate finish Sat Sep 25 21:02:15 2010
  0.21% done, estimate finish Sat Sep 25 20:59:20 2010
  0.23% done, estimate finish Sat Sep 25 20:56:59 2010
  0.26% done, estimate finish Sat Sep 25 20:55:04 2010
  0.28% done, estimate finish Sat Sep 25 20:53:25 2010

mkisofs calculate size command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -print-size -quiet -volid Filmy 1 -volset  -appid K3B THE CD KREATOR (C) 1998-2010 SEBASTIAN TRUEG AND MICHAL MALEK -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-vmonkey/k3bx14169.tmp -rational-rock -hide-list /tmp/kde-vmonkey/k3bX14169.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-vmonkey/k3bJ14169.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 3 -path-list /tmp/kde-vmonkey/k3bT14169.tmp

mkisofs command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -volid Filmy 1 -volset  -appid K3B THE CD KREATOR (C) 1998-2010 SEBASTIAN TRUEG AND MICHAL MALEK -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-vmonkey/k3bv14169.tmp -rational-rock -hide-list /tmp/kde-vmonkey/k3bO14169.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-vmonkey/k3bC14169.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 3 -path-list /tmp/kde-vmonkey/k3bj14169.tmpSo I ask - did anyone find a sollution to this problem? Did anyone experience it?
Best regards,
vmonkey

*edit: Burning process does not burn anything to CDs/DVDs.*

---

### Post by darkstarbyte on 2010-09-27
When you booted Slax did you burn anything.

If I had to guess if the answer to the first one is no then it means you may never be able to burn anything with it again. 

Its common for dvd burners to go out I had a usb one go out on me.

---

### Post by overdrank on 2010-09-27
Moved to Maverick Meerkat Testing and Discussion

---

### Post by recluce on 2010-09-27
It is quite widely accepted that the choice of CD-burning backend (wodim) in Debian/Ubuntu is a political one and that the tools themselves are barely maintained and of poor quality.

I would suggest to install the original, recently updated CDR-Tools from this ppa:

[https://launchpad.net/~brandonsnider/+archive/cdrtools](https://launchpad.net/~brandonsnider/+archive/cdrtools)

I haven't had any trouble with these backends, but lots of trouble with wodim.

---

### Post by mc4man on 2010-09-27
I would definitely give the ppa a try, though I don't believe just adding the ppa will change (update) anything.

After adding the ppa search cdr in synaptic, scroll around and mark cdrecord  and mkisofs for install.
They will be installed, genisoimage and wodim will be removed in such a way to maintain your dependencies for k3b ect.

While you're there you could also mark cdda2wav for install to remove/replace icedax. (used for ripping

(there is also cdrskin as a replacentment for wodim - I'd go for the ppa and mkisofs ect.

There main error seems to be a failure to OPC. (optimum power calibration test), maybe it's true, maybe it's nonsense...

(while there may be some advantage to doing an OPC before burn it's certainly not a necessity

---

### Post by VMC on 2010-09-28
> **recluce said:**
> It is quite widely accepted that the choice of CD-burning backend (wodim) in Debian/Ubuntu is a political one and that the tools themselves are barely maintained and of poor quality.

I would suggest to install the original, recently updated CDR-Tools from this ppa:

[https://launchpad.net/~brandonsnider/+archive/cdrtools](https://launchpad.net/~brandonsnider/+archive/cdrtools)

I haven't had any trouble with these backends, but lots of trouble with wodim.

I didn't know this regarding wodim being of poor quality. 
I have had great results using crdtools in the past. I've never thought of the two in this context. I'll have to do some research, thanks.

---

### Post by vmonkey on 2010-09-28
On Slax the burning application worked (K3b).
I added the mentioned repository and tried to burn a DVD and it gives me another error messages:

Input/output error, not necessarilly serious
Unable to fixate disc

As soon as K3b stops trying to burn, I will post a new log message.

Because in Slax it worked I found a list of it's packages which may be found [here.]("http://www.slax.org/forum.php?action=view&parentID=3702") I hope it may somehow help to find the sollution for my problem.

*edit:*> Devices
-----------------------
hp CDDVDW TS-L633N 0300 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump] [%7]

K3b::IsoImager
-----------------------
mkisofs print size result: 2133900 (4370227200 bytes)

System
-----------------------
K3b Version: 2.0.1
KDE Version: 4.5.1 (KDE 4.5.1)
QT Version:  4.7.0
Kernel:      2.6.35-22-generic

Used versions
-----------------------
mkisofs: 3.0
cdrecord: 3.0

cdrecord
-----------------------
scsidev: '/dev/sr0'
devname: '/dev/sr0'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
SCSI buffer size: 64512
/usr/bin/cdrecord: Warning: Cannot read drive buffer.
/usr/bin/cdrecord: Warning: The DMA speed test has been skipped.
Cdrecord-ProDVD-ProBD-Clone 3.00 (i686-pc-linux-gnu) Copyright (C) 1995-2010 J&#65533;rg Schilling
TOC Type: 1 = CD-ROM
Using libscg version 'schily-0.9'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'hp      '
Identifikation : 'CDDVDW TS-L633N '
Revision       : '0300'
Device seems to be: Generic mmc2 DVD-R/DVD-RW/DVD-RAM.
Current: DVD-R sequential recording
Profile: DVD-R/DL sequential recording 
Profile: DVD-R/DL layer jump recording 
Profile: DVD+R/DL 
Profile: DVD+R 
Profile: DVD+RW 
Profile: DVD-RW sequential recording 
Profile: DVD-RW restricted overwrite 
Profile: DVD-RAM 
Profile: DVD-R sequential recording (current)
Profile: DVD-ROM 
Profile: CD-RW 
Profile: CD-R 
Profile: CD-ROM 
Profile: Removable Disk 
Using generic SCSI-3/mmc-2 DVD-R/DVD-RW/DVD-RAM driver (mmc_dvd).
Driver flags   : NO-CD DVD MMC-3 SWABAUDIO BURNFREE 
Supported modes: PACKET SAO LAYER_JUMP
Drive buf size : 1406976 = 1374 KB
FIFO size      : 4194304 = 4096 KB
Track 01: data  4167 MB        
Total size:     4167 MB = 2133900 sectors
Current Secsize: 2048
Blocks total: 2297888 Blocks current: 2297888 Blocks remaining: 163988
Reducing transfer size from 64512 to 32768 bytes.
Starting to write CD/DVD/BD at speed 8 in real SAO mode for single session.
Last chance to quit, starting real write in 3 seconds.
   2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is OFF.
Turning BURN-Free on
Starting new track at sector: 0
Track 01:    0 of 4167 MB written.
/usr/bin/cdrecord: Input/output error. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 00 00 00 00 00 10 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 72 0B 00 00 00 00 00 0E 09 0C 00 00 00 03 00 00
Sense Key: 0x0 No Additional Sense, Segment 11
Sense Code: 0x00 Qual 0x03 (setmark detected) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 3.845s timeout 200s
/usr/bin/cdrecord: A write error occured.
/usr/bin/cdrecord: Please properly read the error message above.
/usr/bin/cdrecord: Success. test unit ready: scsi sendcmd: no error
CDB:  00 00 00 00 00 00
status: 0x28 (BUSY)
cmd finished after 200.003s timeout 200s
/usr/bin/cdrecord: faio_wait_on_buffer for writer timed out.
/usr/bin/cdrecord: Success. test unit ready: scsi sendcmd: no error
CDB:  00 00 00 00 00 00
status: 0x28 (BUSY)
cmd finished after 200.003s timeout 200s
write track data: error after 0 bytes
Writing  time:  409.386s
Average write speed   7.7x.
Fixating...
/usr/bin/cdrecord: Success. flush cache: scsi sendcmd: no error
CDB:  35 00 00 00 00 00 00 00 00 00
status: 0x28 (BUSY)
cmd finished after 1000.003s timeout 1000s
/usr/bin/cdrecord: Cannot fixate disk.
Trouble flushing the cache
Fixating time: 1000.003s
/usr/bin/cdrecord: Success. prevent/allow medium removal: scsi sendcmd: no error
CDB:  1E 00 00 00 00 00
status: 0x28 (BUSY)
cmd finished after 200.003s timeout 200s
Track 01: data  4167 MB        
Total size:     4167 MB = 2133900 sectors
Current Secsize: 2048
Blocks total: 2297888 Blocks current: 2297888 Blocks remaining: 163988
Reducing transfer size from 64512 to 32768 bytes.
/usr/bin/cdrecord: Success. prevent/allow medium removal: scsi sendcmd: no error
CDB:  1E 00 00 00 00 00
status: 0x28 (BUSY)
cmd finished after 200.004s timeout 200s
/usr/bin/cdrecord: fifo had 128 puts and 1 gets.
/usr/bin/cdrecord: fifo was 0 times empty and 0 times full, min fill was 100%.

cdrecord command:
-----------------------
/usr/bin/cdrecord -v gracetime=2 dev=/dev/sr0 speed=8 -sao driveropts=burnfree -data -tsize=2133900s -

mkisofs
-----------------------
/usr/bin/mkisofs: Warning: Cannot add inode hints with -no-cache-inodes.
2133900
/usr/bin/mkisofs: Warning: Cannot add inode hints with -no-cache-inodes.
Setting input-charset to 'UTF-8' from locale.
  0.02% done, estimate finish Tue Sep 28 11:27:50 2010
  0.05% done, estimate finish Tue Sep 28 09:45:00 2010
  0.07% done, estimate finish Tue Sep 28 09:10:02 2010
  0.09% done, estimate finish Tue Sep 28 08:52:00 2010

mkisofs calculate size command:
-----------------------
/usr/bin/mkisofs -gui -graft-points -print-size -quiet -volid Filmy1 -volset  -appid K3B THE CD KREATOR (C) 1998-2010 SEBASTIAN TRUEG AND MICHAL MALEK -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-vmonkey/k3bPR3410.tmp -rational-rock -hide-list /tmp/kde-vmonkey/k3byV3410.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-vmonkey/k3bJw3410.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 3 -path-list /tmp/kde-vmonkey/k3bUw3410.tmp

mkisofs command:
-----------------------
/usr/bin/mkisofs -gui -graft-points -volid Filmy1 -volset  -appid K3B THE CD KREATOR (C) 1998-2010 SEBASTIAN TRUEG AND MICHAL MALEK -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-vmonkey/k3bBQ3410.tmp -rational-rock -hide-list /tmp/kde-vmonkey/k3buF3410.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-vmonkey/k3bVm3410.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 3 -path-list /tmp/kde-vmonkey/k3bnT3410.tmp


---

### Post by seeker5528 on 2010-09-29
> **recluce said:**
> It is quite widely accepted that the choice of CD-burning backend (wodim) in Debian/Ubuntu is a political one and that the tools themselves are barely maintained and of poor quality.

The question you gotta ask is......

Widely accepted because Wodim is actually poor quality or widely accepted because Schilling has made so many, often vague or irrational, rants about it that people just accept his version of the status?

Later, Seeker

---

### Post by vmonkey on 2010-09-30
Hi all,
thanks for your support!
I decided to make a new and clear installation of Ubuntu. I installed 64-bit version (I used to have 32-bit) and also installed "only" Lucid, not Mavenrick, as it is still beta, and...

IT WORKS THERE!!!!

So I am not sure what exactly was the problem, but my DVD-recorder works.

Thanks

---

