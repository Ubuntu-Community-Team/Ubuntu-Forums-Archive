---
title: "K3b burning problems--cdrecord has no permission to open the device"
date: 2010-12-14
forum: Multimedia Software
---

### Post by puffcorn on 2010-12-14
I was trying to burn an .iso with K3b a little while ago, and had some problems.

First of all, even though I chose 8x to burn my (16x) DVD, it switched to 11x or 12x around halfway through the burning process.

There were also some ticking noises that I'm pretty sure were coming from the DVD writer, not terribly loud, but noticeable.  This had never happened before.

Finally, it got stuck at about 98% (but not frozen, as the time elapsed kept going), and did not finish burning--got an error message (and a bad disc):

"cdrecord has no permission to open the device"

I inspected the disc and there was one dark spot (on the dye) about halfway through the disc, very thin and couple of millimeters long.  (This was present only after burning). 

I'm using Ubuntu 10.04, K3b version 1.91.0, Lite-On DVDRW SHW-160P6S

Here's the output:

```

Devices
-----------------------
LITE-ON DVDRW SHW-160P6S PS09 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump] [%7]

System
-----------------------
K3b Version: 1.91.0
KDE Version: 4.4.2 (KDE 4.4.2)
QT Version:  4.6.2
Kernel:      2.6.32-26-generic

Used versions
-----------------------
cdrecord: 1.1.10

cdrecord
-----------------------
/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
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
Vendor_info    : 'LITE-ON '
Identification : 'DVDRW SHW-160P6S'
Revision       : 'PS09'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0011 (DVD-R sequential recording)
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0011 (DVD-R sequential recording) (current)
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) 
Profile: 0x0008 (CD-ROM) 
Using generic SCSI-3/mmc DVD-R(W) driver (mmc_mdvd).
Driver flags   : SWABAUDIO BURNFREE 
Supported modes: PACKET SAO
Drive buf size : 1182464 = 1154 KB
FIFO size      : 12582912 = 12288 KB
Speed set to 11080 KB/s
Track 01: data  4377 MB        
Total size:     5027 MB (498:07.13) = 2241535 sectors
Lout start:     5028 MB (498:09/10) = 2241535 sectors
Current Secsize: 2048
HINT: use dvd+rw-mediainfo from dvd+rw-tools for information extraction.
Blocks total: 2298496 Blocks current: 2298496 Blocks remaining: 56961
Starting to write CD/DVD at speed   8.0 in real SAO mode for single session.
Last chance to quit, starting real write in    2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Sending CUE sheet...
Starting new track at sector: 0
Track 01:    0 of 4377 MB written.
Track 01:    1 of 4377 MB written (fifo  98%) [buf  99%]   0.1x.
Track 01:    2 of 4377 MB written (fifo  98%) [buf  99%]   6.8x.

... (edited down)

Track 01: 4308 of 4377 MB written (fifo  96%) [buf  98%]  11.4x.
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 21 A9 C2 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 0A 00 00 00 00 0C 00 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x0C Qual 0x00 (write error) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 115.988s timeout 200s
/usr/bin/wodim: A write error occured.
/usr/bin/wodim: Please properly read the error message above.
write track data: error after 4518187008 bytes
Writing  time:  526.192s
Average write speed   6.9x.
Min drive buffer fill was 67%
Fixating...
Fixating time:    0.003s
/usr/bin/wodim: fifo had 71358 puts and 71167 gets.
/usr/bin/wodim: fifo was 0 times empty and 6986 times full, min fill was 58%.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/sr0 speed=8 -sao driveropts=burnfree -data -tsize=2241535s -

```

I've already checked that I'm a member of the cdrom group, and I also have ubuntu-restricted-extras installed.

I doubt it's a bad disc--Taiyo Yuden, which have worked perfectly before. (But you never know, I suppose).

Is there a chance that the DVD drive is going bad?

One thing that I'm wondering--could this have been caused by installing the newest VLC player (1.1.5 via LP-PPA-lucid-bleed repo)?  Doing this removed my installation of Devede--is it possible that it did something to K3b as well?

I'd be happy to include any other info that would be relevant.

Thanks in advance to anyone who can help me on this!

---

### Post by puffcorn on 2010-12-14
Update: It appears it was just a permission problem... I'm not sure how to change the permissions properly, so I ended up running gksudo k3b (because there were a couple of things I wanted to get done), and it ran smoothly and I got a couple of good burns out of it.

I am wondering if someone can tell me how to properly set the permissions on K3b so I don't have to run as root.

---

### Post by davidjmayo on 2010-12-18
> I am wondering if someone can tell me how to properly set the permissions on K3b so I don't have to run as root.

Go into settings, choose "set system preferences". Just accept the suggestions in the column "change". You have to confim each one with an Admin/root password

The settings hold (but I also have the unsolvable 254 error, and it does not fix that)

---

### Post by Ron O on 2011-02-14
One thing that can throw you off is that if you try to add to an open session previously started by Nero or some other Windoze app, you will get a permissions error. If you use a blank CD/DVD within K3b, there is no problem.

---

