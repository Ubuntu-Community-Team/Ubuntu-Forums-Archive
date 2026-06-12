---
title: "Cannot blank a CD-RW"
date: 2011-07-11
forum: Multimedia Software
---

### Post by uqbar on 2011-07-11
I've had to abort a burning process on a CD-RW wirh K3B.
After that I've not been able to either read the medium information or to blank it.
I've also tried to use commandline to do so:
--------
~ sudo cdrecord -v -v -v blank=disk
TOC Type: 1 = CD-ROM
Device was not specified. Trying to find an appropriate drive...
Detected CD-R drive: /dev/cdrw
Using /dev/cdrom of unknown capabilities
scsidev: '/dev/cdrom'
devname: '/dev/cdrom'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.11
Using libusal version 'Cdrkit-1.1.11'.
Driveropts: 'burnfree'
SCSI buffer size: 64512
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identification : 'DVDRAM GSA-T20L '
Revision       : 'NR02'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0000 (Reserved/Unknown)
Profile: 0x0012 (DVD-RAM) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x001A (DVD+RW) 
Profile: 0x001B (DVD+R) 
Profile: 0x002B (DVD+R/DL) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x0009 (CD-R) 
Profile: 0x000A (CD-RW) 
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) 
Supported CD-RW media types: 0F
Drive current speed: 24
Drive default speed: 24
Drive max speed    : 24
Selected speed     : 24
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1966080 = 1920 KB
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
Drive DMA Speed: 13006 kB/s 73x CD 9x DVD
 01 00 00 01 00 00 00 00
 01 AA 01 01 00 00 00 00
Track 1 start -150
 01 00 A0 00 00 00 00 01 00 00 00 00
 01 00 A1 00 00 00 00 00 00 00 00 00
 01 00 A2 00 00 00 00 00 00 00 00 00
Errno: 5 (Input/output error), test unit ready scsi sendcmd: no error
CDB:  00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 02 00 00 00 00 0A 00 00 BB 00 3A 00 00 00
Sense Key: 0x2 Not Ready, Segment 0
Sense Code: 0x3A Qual 0x00 (medium not present) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.003s timeout 40s
wodim: No disk / Wrong disk!
--------
Even going down to speed=1 didn't help!
Now what?

---

### Post by psusi on 2011-07-11
Try a different drive; it looks like that one has a firmware bug.

---

### Post by uqbar on 2011-07-11
Don't think so: it used to work fine under GNOME (11.04) but is now failing under KDE ...
If I ask K3B to "refresh" the medium info window, it doesn't even try to read it.
If I put in a brand new CD-RW, everything is OK. If I put a written one, it's like not inserting anything at all into the drive.
It seems to me that the *-RW media are not recognized any more once written.
Is there any debug I can do?

UPDATE:
I've inserted a brand new CD-RW and managed to burn some music onto it. The medium got recognized as an empty CD-RW.
It can be played by my home CD music player.
If I insert it back into the drive of the PC it's not recognized any more. I've tried also:
~  sudo cdrdao disk-info
Cdrdao version 1.2.3 - (C) Andreas Mueller <andreas@daneb.de>
/dev/sr0: HL-DT-ST DVDRAM GSA-T20L      Rev: NR02
Using driver: Generic SCSI-3/MMC - Version 2.0 (options 0x0000)

WARNING: Unit not ready, still trying...
WARNING: Unit not ready, still trying...
WARNING: Unit not ready, still trying...
WARNING: Unit not ready, still trying...
WARNING: Unit not ready, still trying...
WARNING: Unit not ready, still trying...
WARNING: Unit not ready, still trying...
WARNING: Unit not ready, still trying...
WARNING: Unit not ready, still trying...
WARNING: Unit not ready, still trying...
ERROR: Unit not ready, giving up.
ERROR: Cannot setup device /dev/sr0.

---

### Post by psusi on 2011-07-11
cdrecord and cdrdao do not know or care whether you are running gnome or kde.

I suppose you could try booting 11.04 from a liveusb, and see if it works there, but I very much doubt it.

---

### Post by uqbar on 2011-07-11
> **psusi said:**
> cdrecord and cdrdao do not know or care whether you are running gnome or kde.

I suppose you could try booting 11.04 from a liveusb, and see if it works there, but I very much doubt it.

Correct, but how would you explain the unability to recognize a burnt CD-RW?
Which part of the system is taking care for checking the inserted media? (I have no idea).

---

### Post by jmore9 on 2011-07-11
Try Brasero .  When one doesn't work try one of the others.  there are about 3 more in the repos.

---

### Post by psusi on 2011-07-11
> **uqbar said:**
> Correct, but how would you explain the unability to recognize a burnt CD-RW?
Which part of the system is taking care for checking the inserted media? (I have no idea).

It is up to the drive to figure out if there is media present or not.  It looks like your drive is deciding there isn't wrongly.  You might check your dmesg to see if there are any more detailed errors, or try reading the disk with dd.

sudo dd if=/dev/cdrom of=/dev/null

---

### Post by uqbar on 2011-07-12
> **psusi said:**
> It is up to the drive to figure out if there is media present or not.  It looks like your drive is deciding there isn't wrongly.  You might check your dmesg to see if there are any more detailed errors, or try reading the disk with dd.

sudo dd if=/dev/cdrom of=/dev/null

Good hint. With no result.
It says (in my language which is not English) that there's no medium into either /dev/cdrom or /dev/cdrw.
The syslog says:

Jul 12 08:34:49 uqbar kernel: [  349.588824] sr 7:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
Jul 12 08:34:49 uqbar kernel: [  349.588828] sr 7:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
Jul 12 08:34:49 uqbar kernel: [  349.588836] end_request: I/O error, dev sr1, sector 64
Jul 12 08:34:49 uqbar kernel: [  349.588839] Buffer I/O error on device sr1, logical block 8
Jul 12 08:34:49 uqbar kernel: [  349.619932] sr 7:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul 12 08:34:49 uqbar kernel: [  349.619936] sr 7:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
Jul 12 08:34:49 uqbar kernel: [  349.619939] sr 7:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
Jul 12 08:34:49 uqbar kernel: [  349.619943] sr 7:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
Jul 12 08:34:49 uqbar kernel: [  349.619951] end_request: I/O error, dev sr1, sector 64
Jul 12 08:34:49 uqbar kernel: [  349.619953] Buffer I/O error on device sr1, logical block 8

Has my burner gone? :-(

UPDATE.
I've attached an USB burner.
CD-RWs are recognized and I can see the friendly pop up about the new medium insertion.
But when I try the dd test I get this:

# dd if=/dev/cdrom2 of=/dev/null
dd: lettura di "/dev/cdrom2": Errore di input/output
0+0 record dentro
0+0 record fuori
0 byte (0 B) copiati, 0,066393 s, 0,0 kB/s

And the syslog says:

Jul 12 08:47:08 uqbar kernel: [ 1088.415108] sr 7:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul 12 08:47:08 uqbar kernel: [ 1088.415120] sr 7:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
Jul 12 08:47:08 uqbar kernel: [ 1088.415132] sr 7:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
Jul 12 08:47:08 uqbar kernel: [ 1088.415146] sr 7:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
Jul 12 08:47:08 uqbar kernel: [ 1088.415170] end_request: I/O error, dev sr1, sector 0
Jul 12 08:47:08 uqbar kernel: [ 1088.415179] Buffer I/O error on device sr1, logical block 0
Jul 12 08:47:08 uqbar kernel: [ 1088.415192] Buffer I/O error on device sr1, logical block 1
Jul 12 08:47:08 uqbar kernel: [ 1088.415198] Buffer I/O error on device sr1, logical block 2
Jul 12 08:47:08 uqbar kernel: [ 1088.415205] Buffer I/O error on device sr1, logical block 3
Jul 12 08:47:08 uqbar kernel: [ 1088.446330] sr 7:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jul 12 08:47:08 uqbar kernel: [ 1088.446333] sr 7:0:0:0: [sr1]  Sense Key : Illegal Request [current] 
Jul 12 08:47:08 uqbar kernel: [ 1088.446337] sr 7:0:0:0: [sr1]  Add. Sense: Illegal mode for this track
Jul 12 08:47:08 uqbar kernel: [ 1088.446341] sr 7:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
Jul 12 08:47:08 uqbar kernel: [ 1088.446348] end_request: I/O error, dev sr1, sector 0
Jul 12 08:47:08 uqbar kernel: [ 1088.446351] Buffer I/O error on device sr1, logical block 0

---

### Post by uqbar on 2011-07-12
UPDATE #2.
Any medium other than CD-RW can be burnt and read back with either K3B or brasero.
CD-RWs fail in K3B unless they are brand new (never burnt).
CD-RWs work with brasero at any time: I can erase them, burn anything onto it and finally read the stuff back.

My personal opinion is that K3B writes something wrong onto the CD-RWs and make them unusable for later usage.

---

### Post by psusi on 2011-07-12
Is that a data cd or an audio cd?  You can't dd an audio cd.

If you burn a cd-rw in your original burner with k3b, and it won't be recognized in that drive... will the usb drive recognize it?

---

### Post by uqbar on 2011-07-12
1010101010

---

### Post by uqbar on 2011-07-18
I took more time to make al tests from scratch. And the results are really puzzling.

0. I used to run KDE v3.5 on the same hardware in the past with no issue at all in any case (CD/DVD/R/RW/audio/data).

1. CD-Rs work as either data or audio. The empty media get recognized (the friendly windows pops up saying that I have an empty medium). K3B can burn them. When re-inserted the media can be read back.

2. Brand new CD-RWs can be burnt with K3B (and brasero) as either data or audio.

3. CD-RWs already written don't get recognized by KDE, K3B and Brasero. Just like I had not inserted anyting into the drive. Command line "sudo cdrdao disk-info" says "WARNING: Unit not ready, still trying..." and gives up after 10 attemopts. There's nothing in the syslogs about /dev/sr0.

4. With an external USB burner (/dev/sr1) the written CR-RWs get recognized by both KDE and K3B. Unluckily K3B is not able to clean it, while commandline cdrdao and brasero can do it.

5. Blanked CD-RWs can be writtem by the USB burner but not by the internal one.

6. DVD+/-R and DVD+/-RW always work with the internal burner.

All tests above have been repated 4 times always with the same results.

My own considerations.
If it's a burner issue, it's a weird one.
Maybe there's something weird in the way k3b writes to CD-RWs (alone) which makes them unrecognizable by KDE.

Is there any hint on how to troubleshoot this situation?

---

### Post by psusi on 2011-07-18
Things are getting a little mixed up with multiple discs in multiple states, so let me just get this straight:

You can take a disc that has been written by the original drive before, and that drive now refuses to recognize that the disc is present.  You can then put that same disc in another drive where it is read fine.  You can then erase that disc with the external drive, and then burn it with the external drive.  At that point it can be read by either drive.  If you erase the disc with the external drive, then the internal drive once again refuses to recognize it.

If this is the case, then your original drive has broken firmware.  Have you updated the drive's firmware between the time it originally wrote the disc, and the time it refused to recognize it?

---

### Post by uqbar on 2011-07-18
> **psusi said:**
> Things are getting a little mixed up with multiple discs in multiple states, so let me just get this straight:

You can take a disc that has been written by the original drive before, and that drive now refuses to recognize that the disc is present.  You can then put that same disc in another drive where it is read fine.  You can then erase that disc with the external drive, and then burn it with the external drive.  At that point it can be read by either drive.  If you erase the disc with the external drive, then the internal drive once again refuses to recognize it.
Almost right. The issues are happening only with CD-RWs. I can write CD-RWs in the original drive ONLY WHEN BRAND NEW. And, once written, I cannot read or even get the disk-info with "cdrdao fidk-info" command line.
The writte medium is readable and blankable with an external USB burner.
On the other side, a CD-RW written with the external USB burner is not recognized by the internal burner and cannot be read.
The external USB burner can access it, but with the following information in the logs:

[85152.203058] sr 9:0:0:0: [sr1] Unhandled sense code
[85152.203061] sr 9:0:0:0: [sr1]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[85152.203065] sr 9:0:0:0: [sr1]  Sense Key : Hardware Error [current] 
[85152.203069] sr 9:0:0:0: [sr1]  Add. Sense: Timeout on logical unit
[85152.203073] sr 9:0:0:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[85152.203081] end_request: I/O error, dev sr1, sector 0
[85152.203085] quiet_error: 5 callbacks suppressed
[85152.203087] Buffer I/O error on device sr1, logical block 0

Any other medium is working fine under any circumstance and burner.

> **psusi said:**
> 
If this is the case, then your original drive has broken firmware.  Have you updated the drive's firmware between the time it originally wrote the disc, and the time it refused to recognize it?
I've never update the firmware. The burned could be broken, but then it'd be non working for written CD-RWs only ...

---

