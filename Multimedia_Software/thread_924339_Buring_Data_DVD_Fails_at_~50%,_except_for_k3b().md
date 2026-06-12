---
title: "Buring Data DVD Fails at ~50%, except for k3b(?)"
date: 2008-09-19
forum: Multimedia Software
---

### Post by LonelyAppleHater on 2008-09-19
I went head-first into Ubuntu back in Feb. when my < 2 year old Mac Mini died (hence my nick).  I've been able to do everything and more with Ubuntu, and will never go back to proprietary software again.

Up until now, I haven't had any trouble burning discs at all using the default burning program built into GNOME.  Just like the Mac, but without the $129 updates :)

Last night, though, I was making coasters just making a simple data DVD with DivX files on it to play in my DVD player.  It would burn half-way, then the drive would stop spinning, and I would get an error message.  

I then tried with Brassero. Same exact thing happened.  Looking at the log, I recall lines such as "Flushing Cache" and "Resource Temporarily Unavailable"

Then, I tried GnomeBaker.  Same exact thing with the same error messages in the log.

I thought it was my burner until I tried k3b just for kicks.  It burned just fine. Not sure why, as it seems like they all use growisofs to burn DVD's.

Has anyone had any trouble like this with these GNOME-based disc burn programs and have a solution?  If this isn't enough, I'll be happy to make another coaster in order to post the log here. 

Thanks in advance.

---

### Post by LonelyAppleHater on 2008-09-21
Bump.

No one has any ideas?  I have a LITE-ON 20x DVD burner BTW.  

What's weird is that it was just working again today.  I burned about 5 DVD's and CD's in Brasero and Gnomebaker.  Then I decided to try the Nautilus burn://.  Then it failed.  Now I'm getting all sort of different errors.  I'm getting messages such as: 

"You may have overburned the disc" 
"Cannot open device" 
"You don't have permissions for the device"

I even tried sudo k3b and it still wouldn't burn correctly.

I don't understand why I've been burning discs since February, then it stopped working, then working again, then stopped working a 2nd time.  The only things I've been doing is constantly updating, which I thought improves things, but apparently it doesn't.  

Any suggestions would be greatly appreciated.  Thanks.

---

### Post by LonelyAppleHater on 2008-09-21
Ok, I forgot to copy the log file, but it mentions RLIMIT_MEMLOCK.  I'm assuming this is some sort of lock file I need to clear?  

I'm considering just reinstalling.  Anyone have any ideas?  Thanks in advance.

---

### Post by mc4man on 2008-09-21
I can't help you out at all with linux burning apps (use Imgburn in wine), but 
> RLIMIT_MEMLOCK is referring to the buffer (  exculsive access (locking) to x amount of memory for use as a buffer while burning

---

### Post by LonelyAppleHater on 2008-09-21
Thanks for the reply.

Why do you use imgburn for Windows?  Are there problems with the Linux burn programs that I don't know about?  Anyways, I tried imgburn and it didn't recognize my device.  Maybe because I have a SATA drive?

Here's the output from k3b:

```

System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.9
QT Version:  3.3.8b
Kernel:      2.6.24-19-generic
Devices
-----------------------
LITE-ON DVDRW LH-20A1S 9L08 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump]

K3bIsoImager
-----------------------
mkisofs print size result: 236444 (484237312 bytes)
Pipe throughput: 22329344 bytes read, 22324992 bytes written.

Used versions
-----------------------
mkisofs: 1.1.6
cdrecord: 1.1.6

cdrecord
-----------------------
/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
scsidev: '/dev/scd0'
devname: '/dev/scd0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 3 = CD-ROM XA mode 2
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'LITE-ON '
Identification : 'DVDRW LH-20A1S  '
Revision       : '9L08'
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
Drive buf size : 988416 = 965 KB
FIFO size      : 12582912 = 12288 KB
Track 01: data   461 MB        
Total size:      530 MB (52:32.61) = 236446 sectors
Lout start:      530 MB (52:34/46) = 236446 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type A, high Beta category (A+) (3)
  ATIP start of lead in:  -11634 (97:26/66)
  ATIP start of lead out: 359848 (79:59/73)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 3
Manufacturer: CMC Magnetics Corporation
Blocks total: 359848 Blocks current: 359848 Blocks remaining: 123402
Forcespeed is OFF.
Starting to write CD/DVD at speed  40.0 in real TAO mode for multi session.
Last chance to quit, starting real write in  2 seconds.
Speed set to 7056 KB/s
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Starting new track at sector: 0
Track 01:    0 of  461 MB written.
Track 01:    1 of  461 MB written (fifo  97%) [buf  90%]   3.4x.
Track 01:    2 of  461 MB written (fifo 100%) [buf  98%]  19.6x.
Track 01:    3 of  461 MB written (fifo 100%) [buf  94%]  19.3x.
Track 01:    4 of  461 MB written (fifo 100%) [buf  96%]  20.0x.
Track 01:    5 of  461 MB written (fifo 100%) [buf  97%]  20.0x.
Track 01:    6 of  461 MB written (fifo 100%) [buf  98%]  19.4x.
Track 01:    7 of  461 MB written (fifo 100%) [buf  99%]  20.1x.
Track 01:    8 of  461 MB written (fifo 100%) [buf  99%]  19.5x.
Track 01:    9 of  461 MB written (fifo 100%) [buf  99%]  20.1x.
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 13 41 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 02 00 00 00 00 0A 00 00 00 00 04 01 00 00
Sense Key: 0x2 Not Ready, Segment 0
Sense Code: 0x04 Qual 0x01 (logical unit is in process of becoming ready) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 4.233s timeout 40s
/usr/bin/wodim: A write error occured.
/usr/bin/wodim: Please properly read the error message above.
Errno: 5 (Input/output error), test unit ready scsi sendcmd: no error
CDB:  00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 02 00 00 00 00 0A 00 00 00 00 04 01 00 00
Sense Key: 0x2 Not Ready, Segment 0
Sense Code: 0x04 Qual 0x01 (logical unit is in process of becoming ready) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.125s timeout 40s
Errno: 5 (Input/output error), flush cache scsi sendcmd: no error
CDB:  35 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 02 00 00 00 00 0A 00 00 00 00 04 01 00 00
Sense Key: 0x2 Not Ready, Segment 0
Sense Code: 0x04 Qual 0x01 (logical unit is in process of becoming ready) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.162s timeout 120s
write track data: error after 10094592 bytes
Trouble flushing the cache
Writing  time:   33.595s
Average write speed 214.1x.
Min drive buffer fill was 90%
Fixating...
/usr/bin/wodim: Cannot fixate disk.
Fixating time:    1.650s
/usr/bin/wodim: fifo had 351 puts and 160 gets.
/usr/bin/wodim: fifo was 0 times empty and 125 times full, min fill was 95%.
BURN-Free was never needed.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/scd0 speed=40 -tao driveropts=burnfree -multi -xa -tsize=236444s - 

mkisofs
-----------------------
236444
I: -input-charset not specified, using utf-8 (detected in locale settings)
  0.22% done, estimate finish Sat Sep 20 22:39:30 2008
  0.43% done, estimate finish Sat Sep 20 22:39:30 2008
  0.64% done, estimate finish Sat Sep 20 22:39:30 2008
  0.85% done, estimate finish Sat Sep 20 22:39:30 2008
  1.06% done, estimate finish Sat Sep 20 22:39:30 2008
  1.27% done, estimate finish Sat Sep 20 22:39:30 2008
  1.48% done, estimate finish Sat Sep 20 22:39:30 2008
  1.70% done, estimate finish Sat Sep 20 22:39:30 2008
  1.91% done, estimate finish Sat Sep 20 22:39:30 2008
  2.12% done, estimate finish Sat Sep 20 22:39:30 2008
  2.33% done, estimate finish Sat Sep 20 22:39:30 2008
  2.54% done, estimate finish Sat Sep 20 22:40:09 2008
  2.75% done, estimate finish Sat Sep 20 22:53:25 2008
  2.96% done, estimate finish Sat Sep 20 22:52:26 2008
  3.17% done, estimate finish Sat Sep 20 22:52:06 2008
  3.39% done, estimate finish Sat Sep 20 22:51:18 2008
  3.60% done, estimate finish Sat Sep 20 22:50:36 2008
  3.81% done, estimate finish Sat Sep 20 22:50:26 2008
  4.02% done, estimate finish Sat Sep 20 22:49:52 2008
  4.24% done, estimate finish Sat Sep 20 22:49:43 2008
  4.45% done, estimate finish Sat Sep 20 22:49:14 2008

mkisofs calculate size command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -print-size -quiet -volid ep16 -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-jasonandcris/k3bnYTbPa.tmp -rational-rock -hide-list /tmp/kde-jasonandcris/k3bx9D9Ra.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-jasonandcris/k3bX2I5Ra.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-jasonandcris/k3bs4l6cc.tmp 

mkisofs command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -volid ep16 -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-jasonandcris/k3bI15uCb.tmp -rational-rock -hide-list /tmp/kde-jasonandcris/k3bUKAfnc.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-jasonandcris/k3b9onYSa.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-jasonandcris/k3bok2voc.tmp 


```

There's that "/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits" error again.  I have no clue what this means.  Is my drive faulty?  It seemed to work last night.  Unfortunately, I don't have a LiveCD handy to try.  I guess I'll have to reinstall.  Does anyone have an idea what this means?   Thanks.

---

### Post by mc4man on 2008-09-21
> Anyways, I tried imgburn and it didn't recognize my device There is an issue with wine and 8.04 at least here. If you have blank media or an audio cd in a drive when opening an app in wine 'wine' can lose the drive. The solution is to run winecfg -> drives and if your drive isn't listed there run auto detect.
Open Imgburn without blank media in drive (or have some media with a file system inserted. ) *After* Imgburn  opens then insert your blank media.

> Are there problems with the Linux burn programs that I don't know about well you are posting about just that. Sometimes they work, sometimes they don't, sometimes the burn works everywhere, sometimes not (other Os's, standalone, ect.

Imgburn *always* does a correct job, the only exception is defective blank media 

"Imgburn or how I learned to stop worrying and love burning on linux"

---

### Post by LonelyAppleHater on 2008-09-21
> **mc4man said:**
> There is an issue with wine and 8.04 at least here. If you have blank media or an audio cd in a drive when opening an app in wine 'wine' can lose the drive. The solution is to run winecfg -> drives and if your drive isn't listed there run auto detect.
Open Imgburn without blank media in drive (or have some media with a file system inserted. ) *After* Imgburn  opens then insert your blank media.

 well you are posting about just that. Sometimes they work, sometimes they don't, sometimes the burn works everywhere, sometimes not (other Os's, standalone, ect.

Imgburn *always* does a correct job, the only exception is defective blank media 

"Imgburn or how I learned to stop worrying and love burning on linux"

Thanks again.  I did get the drive to recognize in Imgburn.  Got another coaster though.  So, I think the drive just died, considering that it worked perfectly for a few months and then the drive slowly degraded.  Anyways, this LITE-ON drive vibrates the whole freakin' desk and is extremely loud.  Last time I get a LITE-ON.

I'll post again to see if a new drive works if anyone is interested.  Thanks.

---

### Post by aquamammal on 2008-12-21
I'm interested. My Brasero doesn't even start burning the data DVD!

---

### Post by RJARRRPCGP on 2008-12-21
> **LonelyAppleHater said:**
> Thanks for the reply.

Why do you use imgburn for Windows?  Are there problems with the Linux burn programs that I don't know about?  Anyways, I tried imgburn and it didn't recognize my device.  Maybe because I have a SATA drive?

Here's the output from k3b:

```

System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.9
QT Version:  3.3.8b
Kernel:      2.6.24-19-generic
Devices
-----------------------
LITE-ON DVDRW LH-20A1S 9L08 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump]

K3bIsoImager
-----------------------
mkisofs print size result: 236444 (484237312 bytes)
Pipe throughput: 22329344 bytes read, 22324992 bytes written.

Used versions
-----------------------
mkisofs: 1.1.6
cdrecord: 1.1.6

cdrecord
-----------------------
/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
scsidev: '/dev/scd0'
devname: '/dev/scd0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 3 = CD-ROM XA mode 2
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'LITE-ON '
Identification : 'DVDRW LH-20A1S  '
Revision       : '9L08'
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
Drive buf size : 988416 = 965 KB
FIFO size      : 12582912 = 12288 KB
Track 01: data   461 MB        
Total size:      530 MB (52:32.61) = 236446 sectors
Lout start:      530 MB (52:34/46) = 236446 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type A, high Beta category (A+) (3)
  ATIP start of lead in:  -11634 (97:26/66)
  ATIP start of lead out: 359848 (79:59/73)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 3
Manufacturer: CMC Magnetics Corporation
Blocks total: 359848 Blocks current: 359848 Blocks remaining: 123402
Forcespeed is OFF.
Starting to write CD/DVD at speed  40.0 in real TAO mode for multi session.
Last chance to quit, starting real write in  2 seconds.
Speed set to 7056 KB/s
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Starting new track at sector: 0
Track 01:    0 of  461 MB written.
Track 01:    1 of  461 MB written (fifo  97%) [buf  90%]   3.4x.
Track 01:    2 of  461 MB written (fifo 100%) [buf  98%]  19.6x.
Track 01:    3 of  461 MB written (fifo 100%) [buf  94%]  19.3x.
Track 01:    4 of  461 MB written (fifo 100%) [buf  96%]  20.0x.
Track 01:    5 of  461 MB written (fifo 100%) [buf  97%]  20.0x.
Track 01:    6 of  461 MB written (fifo 100%) [buf  98%]  19.4x.
Track 01:    7 of  461 MB written (fifo 100%) [buf  99%]  20.1x.
Track 01:    8 of  461 MB written (fifo 100%) [buf  99%]  19.5x.
Track 01:    9 of  461 MB written (fifo 100%) [buf  99%]  20.1x.
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 13 41 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 02 00 00 00 00 0A 00 00 00 00 04 01 00 00
Sense Key: 0x2 Not Ready, Segment 0
Sense Code: 0x04 Qual 0x01 (logical unit is in process of becoming ready) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 4.233s timeout 40s
/usr/bin/wodim: A write error occured.
/usr/bin/wodim: Please properly read the error message above.
Errno: 5 (Input/output error), test unit ready scsi sendcmd: no error
CDB:  00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 02 00 00 00 00 0A 00 00 00 00 04 01 00 00
Sense Key: 0x2 Not Ready, Segment 0
Sense Code: 0x04 Qual 0x01 (logical unit is in process of becoming ready) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.125s timeout 40s
Errno: 5 (Input/output error), flush cache scsi sendcmd: no error
CDB:  35 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 02 00 00 00 00 0A 00 00 00 00 04 01 00 00
Sense Key: 0x2 Not Ready, Segment 0
Sense Code: 0x04 Qual 0x01 (logical unit is in process of becoming ready) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.162s timeout 120s
write track data: error after 10094592 bytes
Trouble flushing the cache
Writing  time:   33.595s
Average write speed 214.1x.
Min drive buffer fill was 90%
Fixating...
/usr/bin/wodim: Cannot fixate disk.
Fixating time:    1.650s
/usr/bin/wodim: fifo had 351 puts and 160 gets.
/usr/bin/wodim: fifo was 0 times empty and 125 times full, min fill was 95%.
BURN-Free was never needed.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/scd0 speed=40 -tao driveropts=burnfree -multi -xa -tsize=236444s - 

mkisofs
-----------------------
236444
I: -input-charset not specified, using utf-8 (detected in locale settings)
  0.22% done, estimate finish Sat Sep 20 22:39:30 2008
  0.43% done, estimate finish Sat Sep 20 22:39:30 2008
  0.64% done, estimate finish Sat Sep 20 22:39:30 2008
  0.85% done, estimate finish Sat Sep 20 22:39:30 2008
  1.06% done, estimate finish Sat Sep 20 22:39:30 2008
  1.27% done, estimate finish Sat Sep 20 22:39:30 2008
  1.48% done, estimate finish Sat Sep 20 22:39:30 2008
  1.70% done, estimate finish Sat Sep 20 22:39:30 2008
  1.91% done, estimate finish Sat Sep 20 22:39:30 2008
  2.12% done, estimate finish Sat Sep 20 22:39:30 2008
  2.33% done, estimate finish Sat Sep 20 22:39:30 2008
  2.54% done, estimate finish Sat Sep 20 22:40:09 2008
  2.75% done, estimate finish Sat Sep 20 22:53:25 2008
  2.96% done, estimate finish Sat Sep 20 22:52:26 2008
  3.17% done, estimate finish Sat Sep 20 22:52:06 2008
  3.39% done, estimate finish Sat Sep 20 22:51:18 2008
  3.60% done, estimate finish Sat Sep 20 22:50:36 2008
  3.81% done, estimate finish Sat Sep 20 22:50:26 2008
  4.02% done, estimate finish Sat Sep 20 22:49:52 2008
  4.24% done, estimate finish Sat Sep 20 22:49:43 2008
  4.45% done, estimate finish Sat Sep 20 22:49:14 2008

mkisofs calculate size command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -print-size -quiet -volid ep16 -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-jasonandcris/k3bnYTbPa.tmp -rational-rock -hide-list /tmp/kde-jasonandcris/k3bx9D9Ra.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-jasonandcris/k3bX2I5Ra.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-jasonandcris/k3bs4l6cc.tmp 

mkisofs command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -volid ep16 -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-jasonandcris/k3bI15uCb.tmp -rational-rock -hide-list /tmp/kde-jasonandcris/k3bUKAfnc.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-jasonandcris/k3b9onYSa.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-jasonandcris/k3bok2voc.tmp 


```

There's that "/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits" error again.  I have no clue what this means.  Is my drive faulty?  It seemed to work last night.  Unfortunately, I don't have a LiveCD handy to try.  I guess I'll have to reinstall.  Does anyone have an idea what this means?   Thanks.

Do you ever find your CD drive randomly stop spinning when in middle of reading files, including installing an OS, with it randomly giving you an error message about a file being corrupted, even when the file is fine on the CD or it freezes?

I'm starting to think it's an issue with LiteOn CD drives. But mine does it only when cold. 
I have to warm the bottom of it (hold one of my palms on the bottom of the CD drive until it don't feel cold anymore) with my hands before installing an OS with it,  or I risk it randomly stopping when in middle of reading files!

---

### Post by LonelyAppleHater on 2008-12-21
Sorry I haven't updated this thread.

It was definitely my LITE-ON Drive.  I believe the buffer on the drive started to degrade somehow.  Good thing Newegg has a 1 year return policy on these drives.  I returned it and got an Asus brand instead.  I haven't gotten a coaster since then, and the Asus drives don't seem to vibrate the box as much (I have a SFF Shuttle case). 

So, it was definitely a hardware issue, although I'm sticking with burning everything with Brasero over the Nautilus burner.  

Thanks for everyone's help and interest.

---

### Post by madman100 on 2008-12-22
hi LonelyAppleHater i all so had a problem with my sat writer burning some things and not others re flashed it with the lates firmware and now it fine

---

