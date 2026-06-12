---
title: "Cannot format Dvd-RW in K3B"
date: 2007-12-03
forum: Multimedia &amp; Video
---

### Post by Ltmboy on 2007-12-03
I'm trying to format a Sony Dvd-RW using K3b. K3b tries to and about 3 seconds after I tell it to format the Dvd, it tells me it was successful and that's it's done formating. However, the dvd is not formatted at all, the dvd is still the same, completely full. Here's the log: ```
System
-----------------------
K3b Version: 1.0.3

KDE Version: 3.5.8
QT Version:  3.3.7
Kernel:      2.6.22-14-generic
Devices
-----------------------
MATSHITA DVD-RAM UJ-850S 1.50 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, Restricted Overwrite, Layer Jump]

dvd+rw-format
-----------------------
* BD/DVDÂ±RW/-RAM format utility by <appro@fy.chalmers.se>, version 7.0.
:-( failed to locate "Quick Format" descriptor.
:-( can't locate appropriate format descriptor
* 0.7GB DVD-RW media in Sequential mode detected.
:-[ PERFORM OPC failed with SK=5h/ASC=30h/ACQ=05h]: Wrong medium type
:-[ BLANK failed with SK=5h/ASC=30h/ACQ=05h]: Wrong medium type

dvd+rw-format command:
-----------------------
/usr/bin/dvd+rw-format -gui -blank=full /dev/scd0 

``` :confused: I have no idea what to do to fix this, so any help would be appreciated. Thanks.

---

### Post by mouseboyx on 2007-12-03
You could try installing gnomebaker and do it in there to see if it is a k3b related problem.
```

sudo apt-get install gnomebaker
```

---

### Post by Ltmboy on 2007-12-03
> **mouseboyx said:**
> You could try installing gnomebaker and do it in there to see if it is a k3b related problem.
```

sudo apt-get install gnomebaker
```

Gnomebreaker takes the same amount of time and gives me this as an output: ```
* BD/DVDÂ±RW/-RAM format utility by <appro@fy.chalmers.se>, version 7.0.
:-( can't locate appropriate format descriptor

```

Brasero does the same thing, so maybe I'm missing a file, or a file is corrupted?

---

### Post by Ltmboy on 2007-12-08
Well, I still haven't figured it out. Any more help would be appreciated. Here's Brasero's error log. ```
imager (BraseroLocalImage) set_output
job (BraseroLocalImage) set_task
imager (BraseroLocalImage) get_track
job (BraseroLocalImage) set_task
Session starting:
	flags			= 8531 
	media type	= 0
	speed		= 3
	track type		= 8
	track format	= 2
	output		= none
recorder (BraseroDvdRwFormat) set_drive
recorder (BraseroDvdRwFormat) set_flags
job (BraseroDvdRwFormat) set_task
recorder (BraseroDvdRwFormat) blank
process (BraseroDvdRwFormat) getting varg
dvdformat (BraseroDvdRwFormat) set_action
process (BraseroDvdRwFormat) got varg:
	dvd+rw-format
	-gui
	-blank
	/dev/scd0
process (BraseroDvdRwFormat) launching command
process (BraseroDvdRwFormat) stderr: * BD/DVD
process (BraseroDvdRwFormat) stderr: :-( failed to locate "Quick Format" descriptor.
process (BraseroDvdRwFormat) stderr: :-( can't locate appropriate format descriptor
process (BraseroDvdRwFormat) stderr: * 0.7GB DVD-RW media in Sequential mode detected.
process (BraseroDvdRwFormat) stderr: 0.0%|:-[ PERFORM OPC failed with SK=5h/ASC=30h/ACQ=05h]: Wrong medium type
process (BraseroDvdRwFormat) stderr: :-[ BLANK failed with SK=5h/ASC=30h/ACQ=05h]: Wrong medium type
process (BraseroDvdRwFormat) stderr: HUP
process (BraseroDvdRwFormat) stdout: HUP
job (BraseroDvdRwFormat) asked to stop
	status	= 0
iter (BraseroDvdRwFormat) stopping
process (BraseroDvdRwFormat) got killed
iter (BraseroDvdRwFormat) stopped
job (BraseroDvdRwFormat) got out of loop
job (BraseroDvdRwFormat) set_task
job (BraseroGrowisofs) set_rate
recorder (BraseroGrowisofs) set_drive
recorder (BraseroGrowisofs) set_flags
job (BraseroGrowisofs) set_source
job (BraseroGrowisofs) set_task
recorder (BraseroGrowisofs) record
process (BraseroGrowisofs) getting varg
growisofs (BraseroGrowisofs) set_action
process (BraseroGrowisofs) got varg:
	growisofs
	-use-the-force-luke=notray
	-dvd-compat
	-speed=3
	-use-the-force-luke=tty
	-Z
	/dev/scd0=/home/ltmboy/Desktop/gutsy-desktop-i386.iso
process (BraseroGrowisofs) launching command
process (BraseroGrowisofs) stderr: WARNING: /dev/scd0 already carries isofs!
process (BraseroGrowisofs) stdout: About to execute 'builtin_dd if=/home/ltmboy/Desktop/hardy-desktop-i386.iso of=/dev/scd0 obs=32k seek=0'
process (BraseroGrowisofs) stderr: /dev/scd0: FEATURE 21h is not on, engaging DAO...
process (BraseroGrowisofs) stderr: :-[ PERFORM OPC failed with SK=5h/ASC=30h/ACQ=05h]: Wrong medium type
process (BraseroGrowisofs) stderr: /dev/scd0: reserving 357037 blocks, warning for short DAO recording
process (BraseroGrowisofs) stderr: :-[ RESERVE TRACK failed with SK=5h/ASC=30h/ACQ=05h]: Wrong medium type
process (BraseroGrowisofs) stderr: /dev/scd0: "Current Write Speed" is 3.1x1352KBps.
process (BraseroGrowisofs) stderr: :-[ WRITE@LBA=0h failed with SK=5h/ASC=30h/ACQ=05h]: Wrong medium type
process (BraseroGrowisofs) stderr: :-( media is not formatted or unsupported.
job (BraseroGrowisofs) asked to stop
	status	= 1
	error		= 1
	message	= "Unhandled error, aborting"
iter (BraseroGrowisofs) stopping
process (BraseroGrowisofs) got killed
process (BraseroGrowisofs) stderr: :-( media is not formatted or unsupported.:-( write failed: Wrong medium type
job (BraseroGrowisofs) asked to stop
	status	= 1
	error		= 1
	message	= "Unhandled error, aborting"
iter (BraseroGrowisofs) stopping
iter (BraseroGrowisofs) stopped
job (BraseroGrowisofs) got out of loop
iter (BraseroGrowisofs) stopped
job (BraseroGrowisofs) got out of loop
job (BraseroGrowisofs) set_task
Session error : Unhandled error, aborting
```

---

