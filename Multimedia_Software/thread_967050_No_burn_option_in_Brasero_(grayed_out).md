---
title: "No burn option in Brasero (grayed out)"
date: 2008-11-01
forum: Multimedia Software
---

### Post by supchaka on 2008-11-01
I'm a total noob to Linux/ubuntu, Ive been using it for a week but I am at least smart enough to do some searching first. and I got nothin! :) 

When trying to make a dvd project in brasero my burn button is grayed out no matter what I try. I'm using an AVI as my source file. Ive tried changing the types of my blank media, no go. I downloaded and installed the other recommended items in the help file via synaptic ie: GStreamers plugins, ffmpeg, vcdimager and dvdauthor.

I thought maybe my user wasnt in the cdrom group but it is. The only other thing I can think is my fstab needs something? Here it is

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=cf923d56-b33b-4291-94da-7d6e3be9907a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=981348e8-9fa9-4b14-a581-4a94fe5b3842 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1	/media/storage	ext3	defaults	0	0

In my uneducated guess I'm thinking I need a reference that looks like
/dev/dvd0 /media/dvdrw? Im totaly grasping at straws here but at least wanted to show I'm trying :) Thanks for any ideas!

---

### Post by gruss on 2008-12-26
bump??  same issue here, I have all the plugins installed, movies play fine and I even tried running Brasero as root??

---

### Post by wolfen69 on 2008-12-26
this won't solve your brasero problem, but have you tried K3B for burning? i think it's one of the best i've tried. it can't hurt.

---

### Post by FXEF on 2008-12-26
The burn button is greyed out untill files have been added to the project. When files have been added to the project in the right pane, the burn button becomes active.

---

### Post by gruss on 2008-12-26
I'll try that wolfen and see if it works, don't really have a preference just wanted to burn a movie...love the quote too, my kids play with this new "intrepid" pc and an old xubuntu 6.xx laptop along with an xp notbook.  Kinda funny when they fight over the linux box ;)  its usually for tux paint but hey I like to give them options!

fxef: yes the first button stays greyed out unti the vid is added and shows up but, when I click it and get to the second screen the button never becomes "active"

Edit: K3B is working, thanks.

---

### Post by chiefchief on 2008-12-27
Hey everybody, happy holidays and all that stuff.

I'm experiencing the same problem.  I'll use the workaround with k3b, but this is definitely a bug.  We have 3 people on these forums experiencing the same problem.  Don't suppose anybody wants to attempt a solution?  Or even knows where to start troublshooting this?

Also, I don't think it has anything to do with the fstab, the problem is still there if you try to burn with an image file.

---

### Post by wolfen69 on 2008-12-27
> **chiefchief said:**
>  I'll use the workaround with k3b

i personally, would not call it a workaround, as k3b is a suitable *replacement* for brasero. use what works.

---

### Post by Coder543 on 2008-12-27
You were trying to burn the .avi as if it were a dvd. This doesn't work because a dvd player wouldn't know what to do with an avi. If you did a data project then you could burn it and put it in another computer to view.

---

### Post by 5BallJuggler on 2008-12-27
I've had a similar issue with Brasero and k3b, they will not burn DVD-R disks, the only way I could do that was to use Gnome-Baker.

---

### Post by CoercibleGerm on 2008-12-28
> **chiefchief said:**
>  We have 3 people on these forums experiencing the same problem.

Make that 4.

---

### Post by icyest on 2008-12-28
> **Coder543 said:**
> You were trying to burn the .avi as if it were a dvd. This doesn't work because a dvd player wouldn't know what to do with an avi. If you did a data project then you could burn it and put it in another computer to view.

AVI's are the most popular and most common format that people have for movies on their hard drive. What do you suppose we do with all our AVIs? converting them with HANDBREAK to  mp4 only makes the files bigger, and my computer only reads 700mb disks. Movies are around 700 mb in avi's.


It appears that many people have this problem.

---

### Post by gruss on 2008-12-29
it can't just be burned to a DVD though and play...DeVeDe will convert for ya if you need it to.  Brasero wouldnt let me burn anything...K3B is nice though so I'll give the Brasero folks a try in a few months.

---

### Post by maks_zbogar on 2009-01-09
On my Intrepid, Brasero's second "burn button" is grayed too. I to expect that dvd burning software should convert avi's to mpeg on it's own, before burning dvd video disc. These are small but important things that made me keep my 6 years old win xp computer with Nero burning software.

---

### Post by becominglumberg on 2009-04-28
Mine is jacked up as well, for both avis and mpegs. This is certainly a bug, and it needs to be fixed.

---

### Post by Arup on 2009-04-28
I have a SATA and IDE burner and from 8.01 to 9.04 I have had absolutely no issues burning CDs, DVDs etc of different type from movies to music to mp3.

---

### Post by ChubbySauce on 2009-09-30
make that six

---

### Post by indiecast on 2009-12-04
[http://staghacks.com/?p=334](http://staghacks.com/?p=334)

This should make that button "not grey".

---

### Post by shamimkhaliq on 2010-03-05
make that 7 people with the can't burn DVD-R data files problem

---

### Post by Yellow Pasque on 2010-03-05
Start brasero from the terminal. Does it give any error messages?

---

### Post by tava0002 on 2010-03-09
Make that 8.  

The blank media (cd or dvd) is not always recognized in Brasero and never recognized in K3B.  I verified that all the software in the above link is installed.

I tried running Brasero and K3b from the cli and have the same problem.

I used devede to create an iso and I'm trying to burn it to dvd.

---

### Post by tava0002 on 2010-03-09
I rebooted the machine then started Brasero and selected the .iso to burn, then I put in a cd-r and after about 30 seconds it was recognized.  

After I clicked burn it appeared to work when I got an error with Brasero:

```
Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1848)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI output set (IMAGE) image = /tmp/brasero_tmp_JGPI9U.bin toc = none
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI no burn:// URI found
BraseroBurnURI stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_set_output_size_for_current_track
BraseroLocalTrack stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack output set (IMAGE) image = /tmp/brasero_tmp_9IPI9U.bin toc = none
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack no remote URIs
BraseroLocalTrack stopping
BraseroWodim called brasero_job_get_action
BraseroWodim getting varg
BraseroWodim called brasero_job_get_action
BraseroWodim got varg:
BraseroWodim deactivating
BraseroWodim called brasero_job_get_action
BraseroWodim getting varg
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_get_device
BraseroWodim called brasero_job_get_flags
BraseroWodim called brasero_job_get_speed
BraseroWodim called brasero_job_get_flags
BraseroWodim called brasero_job_get_input_type
BraseroWodim called brasero_job_get_fd_in
BraseroWodim called brasero_job_get_current_track
BraseroWodim called brasero_job_set_current_action
BraseroWodim got varg:
	wodim
	-v
	dev=/dev/sr0
	speed=40
	driveropts=burnfree
	fs=16m
	-data
	-nopad
	/home/tava/Desktop/test/test.iso
BraseroWodim Launching command
BraseroWodim called brasero_job_get_fd_out
BraseroWodim stderr: wodim: No write mode specified.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Asuming -tao mode.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Future versions of wodim may have different drive dependent defaults.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/sr0'
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: devname: '/dev/sr0'
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: scsibus: -2 target: -2 lun: -2
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Linux sg driver version: 3.5.27
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Wodim version: 1.1.9
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: SCSI buffer size: 64512
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: communication breaks or freezes immediately after that.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: TOC Type: 1 = CD-ROM
BraseroWodim stdout: Driveropts: 'burnfree'
BraseroWodim stdout: Device type    : Removable CD-ROM
BraseroWodim stdout: Version        : 5
BraseroWodim stdout: Response Format: 2
BraseroWodim stdout: Capabilities   : 
BraseroWodim stdout: Vendor_info    : 'BENQ    '
BraseroWodim stdout: Identification : 'DVD DD DW1620   '
BraseroWodim stdout: Revision       : 'B7W9'
BraseroWodim stdout: Device seems to be: Generic mmc2 DVD-R/DVD-RW.
BraseroWodim stdout: Current: 0x0009 (CD-R)
BraseroWodim stdout: Profile: 0x002B (DVD+R/DL) 
BraseroWodim stdout: Profile: 0x001B (DVD+R) 
BraseroWodim stdout: Profile: 0x001A (DVD+RW) 
BraseroWodim stdout: Profile: 0x0014 (DVD-RW sequential recording) 
BraseroWodim stdout: Profile: 0x0011 (DVD-R sequential recording) 
BraseroWodim stdout: Profile: 0x0010 (DVD-ROM) 
BraseroWodim stdout: Profile: 0x000A (CD-RW) 
BraseroWodim stdout: Profile: 0x0009 (CD-R) (current)
BraseroWodim stdout: Profile: 0x0008 (CD-ROM) 
BraseroWodim stdout: Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
BraseroWodim stdout: Driver flags   : MMC-3 SWABAUDIO BURNFREE 
BraseroWodim stdout: Supported modes: TAO PACKET SAO SAO/R96R RAW/R16 RAW/R96R
BraseroWodim stdout: Drive buf size : 1073152 = 1048 KB
BraseroWodim stdout: FIFO size      : 16777216 = 16384 KB
BraseroWodim stderr: Speed set to 7056 KB/s
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Track 01: data   415 MB        
BraseroWodim stdout: Total size:      477 MB (47:17.93) = 212845 sectors
BraseroWodim stdout: Lout start:      477 MB (47:19/70) = 212845 sectors
BraseroWodim stdout: Current Secsize: 2048
BraseroWodim stdout: ATIP info from disk:
BraseroWodim stdout:   Indicated writing power: 5
BraseroWodim stdout:   Is not unrestricted
BraseroWodim stdout:   Is not erasable
BraseroWodim stdout:   Disk sub type: Medium Type A, high Beta category (A+) (3)
BraseroWodim stdout:   ATIP start of lead in:  -11634 (97:26/66)
BraseroWodim stdout:   ATIP start of lead out: 359846 (79:59/71)
BraseroWodim stdout: Disk type:    Short strategy type (Phthalocyanine or similar)
BraseroWodim stdout: Manuf. index: 3
BraseroWodim stdout: Manufacturer: CMC Magnetics Corporation
BraseroWodim stdout: Blocks total: 359846 Blocks current: 359846 Blocks remaining: 147001
BraseroWodim stdout: Starting to write CD/DVD at speed  40.0 in real TAO mode for single session.
BraseroWodim stdout: Last chance to quit, starting real write in    4 seconds.
BraseroWodim called brasero_job_set_dangerous
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout:    3 seconds.
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout:    2 seconds.
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout:    1 seconds.   0 seconds. Operation starts.
BraseroWodim stdout: Waiting for reader process to fill input buffer ... input buffer ready.
BraseroWodim stdout: Performing OPC...
[COLOR="Red"]BraseroWodim stderr: Errno: 5 (Input/output error), send opc scsi sendcmd: no error
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: CDB:  54 01 00 00 00 00 00 00 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Writing  time:    9.460s
BraseroWodim stderr: status: 0x2 (CHECK CONDITION)
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Bytes: 70 00 04 00 00 00 00 12 00 00 00 00 09 00 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Key: 0x4 Hardware Error, Segment 0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Code: 0x09 Qual 0x00 (track following error) Fru 0x0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense flags: Blk 0 (not valid) 
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: cmd finished after 9.427s timeout 60s
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: OPC failed.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: fifo had 255 puts and 0 gets.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: fifo was 0 times empty and 0 times full, min fill was 100%.[/COLOR]
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: HUP
BraseroWodim stderr: HUP
BraseroWodim process finished with status 255
BraseroWodim called brasero_job_error
BraseroWodim finished with an error
BraseroWodim asked to stop because of an error
	error		= 0
	message	= "no message"
BraseroWodim stopping
BraseroWodim got killed
Session error : unknown (brasero_burn_record brasero-burn.c:2811)
```


And an error with K3B:

```
Devices
-----------------------
BENQ DVD DD DW1620 B7W9 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96R, RAW/R16, RAW/R96R, Restricted Overwrite] [%7]

System
-----------------------
K3b Version: 1.68.0
KDE Version: 4.3.2 (KDE 4.3.2)
QT Version:  4.5.2
Kernel:      2.6.31-19-generic

Used versions
-----------------------
cdrecord: 1.1.9

cdrecord
-----------------------
/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/sr0'
devname: '/dev/sr0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.9
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 1 = CD-ROM
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'BENQ    '
Identification : 'DVD DD DW1620   '
Revision       : 'B7W9'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009 (CD-R)
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96R RAW/R16 RAW/R96R
Drive buf size : 1073152 = 1048 KB
FIFO size      : 12582912 = 12288 KB
Errno: 5 (Input/output error), start/stop unit scsi sendcmd: no error
CDB:  1B 00 00 00 01 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 04 00 00 00 00 12 00 00 00 00 09 00 00 00
Sense Key: 0x4 Hardware Error, Segment 0
Sense Code: 0x09 Qual 0x00 (track following error) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 1.755s timeout 200s
Errno: 5 (Input/output error), start/stop unit scsi sendcmd: no error
CDB:  1B 00 00 00 01 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 04 00 00 00 00 12 00 00 00 00 09 00 00 00
Sense Key: 0x4 Hardware Error, Segment 0
Sense Code: 0x09 Qual 0x00 (track following error) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 1.773s timeout 200s
Speed set to 7056 KB/s
Track 01: data   415 MB        
Total size:      477 MB (47:17.90) = 212843 sectors
Lout start:      477 MB (47:19/68) = 212843 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type A, high Beta category (A+) (3)
  ATIP start of lead in:  -11634 (97:26/66)
  ATIP start of lead out: 359846 (79:59/71)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 3
Manufacturer: CMC Magnetics Corporation
Blocks total: 359846 Blocks current: 359846 Blocks remaining: 147003
Starting to write CD/DVD at speed  40.0 in real SAO mode for single session.
Last chance to quit, starting real write in    2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Errno: 5 (Input/output error), send opc scsi sendcmd: no error
CDB:  54 01 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 04 00 00 00 00 12 00 00 00 00 09 00 00 00
Sense Key: 0x4 Hardware Error, Segment 0
Sense Code: 0x09 Qual 0x00 (track following error) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 4.258s timeout 200s
/usr/bin/wodim: OPC failed.
Writing  time:    4.292s
/usr/bin/wodim: fifo had 192 puts and 0 gets.
/usr/bin/wodim: fifo was 0 times empty and 0 times full, min fill was 100%.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/sr0 speed=40 -sao driveropts=burnfree -data -tsize=212843s -
```

---

### Post by tava0002 on 2010-03-09
They both have RLIMIT_MEMLOCK errors, looks like a known issue:

[https://lists.ubuntu.com/archives/ubuntu-burning/2009-January/006973.html]("https://lists.ubuntu.com/archives/ubuntu-burning/2009-January/006973.html")

---

