---
title: "burning problem?!?!?!"
date: 2006-12-07
forum: Multimedia &amp; Video
---

### Post by little cazy on 2006-12-07
i've got a burner with an aditode
it reads dvd,cd,and everything else fine
but when it's told to burn something it dosen't
on one program (i've tryed multitple progarms) it show this
> imager (BraseroLocalImage) set_output
job (BraseroLocalImage) set_task
imager (BraseroLocalImage) get_track
job (BraseroLocalImage) set_task
imager (BraseroBurnSum) set_output
job (BraseroBurnSum) set_task
imager (BraseroBurnSum) get_track
sum (BraseroBurnSum) connect_to_clock
sum (BraseroBurnSum) set_action
sum (BraseroBurnSum) start_progress
sum (BraseroBurnSum) set_written
job (BraseroBurnSum) asked to stop
	status	= 0
iter (BraseroBurnSum) stopping
sum (BraseroBurnSum) disconnect_from_clock
iter (BraseroBurnSum) stopped
job (BraseroBurnSum) got out of loop
job (BraseroBurnSum) set_task
Session starting:
	flags			= 16759 
	media type	= 0
	speed		= 2
	track type		= 6
	track format	= 3
	output		= none
job (BraseroGrowisofs) set_source
imager (BraseroGrowisofs) set_output_type
recorder (BraseroGrowisofs) set_drive
imager (BraseroGrowisofs) set_output
imager (BraseroGrowisofs) unsupported operation (in brasero_imager_set_output at burn-imager.c:142)
job (BraseroGrowisofs) set_task
imager (BraseroGrowisofs) get_size
process (BraseroGrowisofs) getting varg
growisofs (BraseroGrowisofs) set_action
process (BraseroGrowisofs) got varg:
	growisofs
	-use-the-force-luke=notray
	-dvd-compat
	-use-the-force-luke=tty
	-Z
	/dev/hdc
	-dry-run
	-r
	-J
	-input-charset
	utf8
	-graft-points
	-D
	-path-list
	/tmp/brasero_tmp_jvfgv9/brasero_tmp_AATAKT
	-exclude-list
	/tmp/brasero_tmp_jvfgv9/brasero_tmp_7CTAKT
	-print-size
process (BraseroGrowisofs) launching command
process (BraseroGrowisofs) stdout: Executing 'mkisofs -r -J -input-charset utf8 -graft-points -D -path-list /tmp/brasero_tmp_jvfgv9/brasero_tmp_AATAKT -exclude-list /tmp/brasero_tmp_jvfgv9/brasero_tmp_7CTAKT -print-size | builtin_dd of=/dev/hdc obs=32k seek=0'
process (BraseroGrowisofs) stderr: Total extents scheduled to be written = 1922464
growisofs (BraseroGrowisofs) set_total
process (BraseroGrowisofs) stdout: HUP
process (BraseroGrowisofs) stderr: HUP
job (BraseroGrowisofs) asked to stop
	status	= 0
iter (BraseroGrowisofs) stopping
process (BraseroGrowisofs) got killed
iter (BraseroGrowisofs) stopped
job (BraseroGrowisofs) got out of loop
job (BraseroGrowisofs) set_task
job (BraseroGrowisofs) set_rate
recorder (BraseroGrowisofs) set_drive
recorder (BraseroGrowisofs) set_flags
job (BraseroGrowisofs) set_task
recorder (BraseroGrowisofs) record
process (BraseroGrowisofs) getting varg
growisofs (BraseroGrowisofs) set_action
process (BraseroGrowisofs) got varg:
	growisofs
	-use-the-force-luke=notray
	-use-the-force-luke=dao
	-speed=2
	-dvd-compat
	-use-the-force-luke=tty
	-use-the-force-luke=tracksize:1922464
	-Z
	/dev/hdc
	-r
	-J
	-input-charset
	utf8
	-graft-points
	-D
	-path-list
	/tmp/brasero_tmp_jvfgv9/brasero_tmp_AATAKT
	-exclude-list
	/tmp/brasero_tmp_jvfgv9/brasero_tmp_7CTAKT
	-V
	Data disc #1
	-A
	Brasero-0.5.1
	-sysid
	LINUX
	-v
process (BraseroGrowisofs) launching command
process (BraseroGrowisofs) stdout: Executing 'mkisofs -r -J -input-charset utf8 -graft-points -D -path-list /tmp/brasero_tmp_jvfgv9/brasero_tmp_AATAKT -exclude-list /tmp/brasero_tmp_jvfgv9/brasero_tmp_7CTAKT -V Data disc #1 -A Brasero-0.5.1 -sysid LINUX -v | builtin_dd of=/dev/hdc obs=32k seek=0'
process (BraseroGrowisofs) stderr: mkisofs 2.01.01a03-unofficial-iconv (i686-pc-linux-gnu)
process (BraseroGrowisofs) stderr: Scanning 
process (BraseroGrowisofs) stderr: Writing:   Initial Padblock                        Start Block 0
process (BraseroGrowisofs) stderr: Done with: Initial Padblock                        Block(s)    16
process (BraseroGrowisofs) stderr: Writing:   Primary Volume Descriptor               Start Block 16
process (BraseroGrowisofs) stderr: Done with: Primary Volume Descriptor               Block(s)    1
process (BraseroGrowisofs) stderr: Writing:   Joliet Volume Descriptor                Start Block 17
process (BraseroGrowisofs) stderr: Done with: Joliet Volume Descriptor                Block(s)    1
process (BraseroGrowisofs) stderr: Writing:   End Volume Descriptor                   Start Block 18
process (BraseroGrowisofs) stderr: Done with: End Volume Descriptor                   Block(s)    1
process (BraseroGrowisofs) stderr: Writing:   Version block                           Start Block 19
process (BraseroGrowisofs) stderr: Done with: Version block                           Block(s)    1
process (BraseroGrowisofs) stderr: Writing:   Path table                              Start Block 20
process (BraseroGrowisofs) stderr: Done with: Path table                              Block(s)    4
process (BraseroGrowisofs) stderr: Writing:   Joliet path table                       Start Block 24
process (BraseroGrowisofs) stderr: Done with: Joliet path table                       Block(s)    4
process (BraseroGrowisofs) stderr: Writing:   Directory tree                          Start Block 28
process (BraseroGrowisofs) stderr: Done with: Directory tree                          Block(s)    153
process (BraseroGrowisofs) stderr: Writing:   Joliet directory tree                   Start Block 181
process (BraseroGrowisofs) stderr: Done with: Joliet directory tree                   Block(s)    118
process (BraseroGrowisofs) stderr: Writing:   Directory tree cleanup                  Start Block 299
process (BraseroGrowisofs) stderr: Done with: Directory tree cleanup                  Block(s)    0
process (BraseroGrowisofs) stderr: Writing:   Extension record                        Start Block 299
process (BraseroGrowisofs) stderr: Done with: Extension record                        Block(s)    1
process (BraseroGrowisofs) stderr: Writing:   The File(s)                             Start Block 300
process (BraseroGrowisofs) stderr:   0.26% done, estimate finish Thu Dec  7 20:07:41 2006
growisofs (BraseroGrowisofs) set_total
growisofs (BraseroGrowisofs) set_written
growisofs (BraseroGrowisofs) set_progress
growisofs (BraseroGrowisofs) set_action
growisofs (BraseroGrowisofs) start_progress
process (BraseroGrowisofs) stderr:   0.52% done, estimate finish Thu Dec  7 20:04:29 2006
growisofs (BraseroGrowisofs) set_total
growisofs (BraseroGrowisofs) set_written
growisofs (BraseroGrowisofs) set_progress
growisofs (BraseroGrowisofs) set_action
growisofs (BraseroGrowisofs) start_progress
process (BraseroGrowisofs) stderr:   0.78% done, estimate finish Thu Dec  7 20:03:25 2006
growisofs (BraseroGrowisofs) set_total
growisofs (BraseroGrowisofs) set_written
growisofs (BraseroGrowisofs) set_progress
growisofs (BraseroGrowisofs) set_action
growisofs (BraseroGrowisofs) start_progress
process (BraseroGrowisofs) stderr: /dev/hdc: engaging DVD-R DAO upon user request...
process (BraseroGrowisofs) stderr: /dev/hdc: reserving 1922464 blocks
process (BraseroGrowisofs) stderr: :-[ RESERVE TRACK failed with SK=5h/ASC=2Ch/ACQ=00h]: Input/output error
process (BraseroGrowisofs) stderr: /dev/hdc: "Current Write Speed" is 2.0x1385KBps.
process (BraseroGrowisofs) stderr: :-? resuming track#1 from LBA#103152
process (BraseroGrowisofs) stderr:   1.04% done, estimate finish Thu Dec  7 20:28:30 2006
growisofs (BraseroGrowisofs) set_total
growisofs (BraseroGrowisofs) set_written
growisofs (BraseroGrowisofs) set_progress
growisofs (BraseroGrowisofs) set_action
growisofs (BraseroGrowisofs) start_progress
process (BraseroGrowisofs) stderr:   1.30% done, estimate finish Thu Dec  7 20:23:03 2006
growisofs (BraseroGrowisofs) set_total
growisofs (BraseroGrowisofs) set_written
growisofs (BraseroGrowisofs) set_progress
growisofs (BraseroGrowisofs) set_action
growisofs (BraseroGrowisofs) start_progress
process (BraseroGrowisofs) stderr:   1.56% done, estimate finish Thu Dec  7 20:20:30 2006
growisofs (BraseroGrowisofs) set_total
growisofs (BraseroGrowisofs) set_written
growisofs (BraseroGrowisofs) set_progress
growisofs (BraseroGrowisofs) set_action
growisofs (BraseroGrowisofs) start_progress
process (BraseroGrowisofs) stderr:   1.82% done, estimate finish Thu Dec  7 20:17:45 2006
growisofs (BraseroGrowisofs) set_total
growisofs (BraseroGrowisofs) set_written
growisofs (BraseroGrowisofs) set_progress
growisofs (BraseroGrowisofs) set_action
growisofs (BraseroGrowisofs) start_progress
process (BraseroGrowisofs) stderr:   2.08% done, estimate finish Thu Dec  7 20:15:41 2006
growisofs (BraseroGrowisofs) set_total
growisofs (BraseroGrowisofs) set_written
growisofs (BraseroGrowisofs) set_progress
growisofs (BraseroGrowisofs) set_action
growisofs (BraseroGrowisofs) start_progress
process (BraseroGrowisofs) stderr:   2.34% done, estimate finish Thu Dec  7 20:14:48 2006
growisofs (BraseroGrowisofs) set_total
growisofs (BraseroGrowisofs) set_written
growisofs (BraseroGrowisofs) set_progress
growisofs (BraseroGrowisofs) set_action
growisofs (BraseroGrowisofs) start_progress
process (BraseroGrowisofs) stderr:   2.60% done, estimate finish Thu Dec  7 20:13:27 2006
growisofs (BraseroGrowisofs) set_total
growisofs (BraseroGrowisofs) set_written
growisofs (BraseroGrowisofs) set_progress
growisofs (BraseroGrowisofs) set_action
growisofs (BraseroGrowisofs) start_progress
process (BraseroGrowisofs) stderr:   2.86% done, estimate finish Thu Dec  7 20:12:20 2006
growisofs (BraseroGrowisofs) set_total
growisofs (BraseroGrowisofs) set_written
growisofs (BraseroGrowisofs) set_progress
growisofs (BraseroGrowisofs) set_action
growisofs (BraseroGrowisofs) start_progress
process (BraseroGrowisofs) stderr:   3.12% done, estimate finish Thu Dec  7 20:11:57 2006
growisofs (BraseroGrowisofs) set_total
growisofs (BraseroGrowisofs) set_written
growisofs (BraseroGrowisofs) set_progress
growisofs (BraseroGrowisofs) set_action
growisofs (BraseroGrowisofs) start_progress
process (BraseroGrowisofs) stderr:   3.38% done, estimate finish Thu Dec  7 20:11:08 2006
growisofs (BraseroGrowisofs) set_total
growisofs (BraseroGrowisofs) set_written
growisofs (BraseroGrowisofs) set_progress
growisofs (BraseroGrowisofs) set_action
growisofs (BraseroGrowisofs) start_progress
process (BraseroGrowisofs) stderr:   3.64% done, estimate finish Thu Dec  7 20:10:53 2006
growisofs (BraseroGrowisofs) set_total
growisofs (BraseroGrowisofs) set_written
growisofs (BraseroGrowisofs) set_progress
growisofs (BraseroGrowisofs) set_action
growisofs (BraseroGrowisofs) start_progress
process (BraseroGrowisofs) stderr:   3.90% done, estimate finish Thu Dec  7 20:10:15 2006
growisofs (BraseroGrowisofs) set_total
growisofs (BraseroGrowisofs) set_written
growisofs (BraseroGrowisofs) set_progress
growisofs (BraseroGrowisofs) set_action
growisofs (BraseroGrowisofs) start_progress
process (BraseroGrowisofs) stderr:   4.16% done, estimate finish Thu Dec  7 20:09:41 2006
growisofs (BraseroGrowisofs) set_total
growisofs (BraseroGrowisofs) set_written
growisofs (BraseroGrowisofs) set_progress
growisofs (BraseroGrowisofs) set_action
growisofs (BraseroGrowisofs) start_progress
process (BraseroGrowisofs) stderr:   4.42% done, estimate finish Thu Dec  7 20:09:34 2006
growisofs (BraseroGrowisofs) set_total
growisofs (BraseroGrowisofs) set_written
growisofs (BraseroGrowisofs) set_progress
growisofs (BraseroGrowisofs) set_action
growisofs (BraseroGrowisofs) start_progress
process (BraseroGrowisofs) stderr:   4.68% done, estimate finish Thu Dec  7 20:09:06 2006
growisofs (BraseroGrowisofs) set_total
growisofs (BraseroGrowisofs) set_written
growisofs (BraseroGrowisofs) set_progress
growisofs (BraseroGrowisofs) set_action
growisofs (BraseroGrowisofs) start_progress
process (BraseroGrowisofs) stderr:   4.94% done, estimate finish Thu Dec  7 20:09:02 2006
growisofs (BraseroGrowisofs) set_total
growisofs (BraseroGrowisofs) set_written
growisofs (BraseroGrowisofs) set_progress
growisofs (BraseroGrowisofs) set_action
growisofs (BraseroGrowisofs) start_progress
process (BraseroGrowisofs) stderr:   5.20% done, estimate finish Thu Dec  7 20:08:39 2006
growisofs (BraseroGrowisofs) set_total
growisofs (BraseroGrowisofs) set_written
growisofs (BraseroGrowisofs) set_progress
growisofs (BraseroGrowisofs) set_action
growisofs (BraseroGrowisofs) start_progress
process (BraseroGrowisofs) stderr: :-[ WRITE@LBA=192f0h failed with SK=5h/ASC=64h/ACQ=00h]: Input/output error
process (BraseroGrowisofs) stderr: :-( write failed: Input/output error
job (BraseroGrowisofs) asked to stop
	status	= 1
	error		= 1
	message	= "Unhandled error, aborting"
iter (BraseroGrowisofs) stopping
process (BraseroGrowisofs) got killed
iter (BraseroGrowisofs) stopped
job (BraseroGrowisofs) got out of loop
job (BraseroGrowisofs) set_task
Session error : Unhandled error, aborting

it will not burn ANYTHING, data disk, DVDs, CDs ](*,) ](*,)

---

### Post by K.Mandla on 2006-12-07
It looks like it's trying. Are you sure there's not a hardware problem with the drive?

I'd try setting the write speed way down, like 4x or slower, or maybe trying a different kind of media.

---

### Post by little cazy on 2006-12-08
i got this last chirstmas so it shouldn't be to old (or broken)
and i  put it at 2x for the data disks i use before
the thing happen before it had a ploblem like this but i reformated
and was able to get one data disk in (all it had was a few ads cause it was a test)

---

### Post by scoon on 2006-12-08
Hey there, 

If this is an ide burner, try putting it as a master on its own ide bus. This link may give you some other good advice:
[http://cdrecord.berlios.de/old/private/man/cdr_readme.html]("http://cdrecord.berlios.de/old/private/man/cdr_readme.html")

-scoon

---

### Post by Artemis3 on 2006-12-08
I have found a serious problem with burning with Edgy Eft. It happens to me with different programs: Nautilus, GnomeBaker, Graveman, and Brasero when it worked (current version doesn't).

When i start the system, it burns one disc. After that, it makes coaster. After restarting the system, i can burn another disc fine, and after that coasters again. (eg. Nautilus / Graveman gives errors) I have repeated this pattern 3 times already and my mountain of coasters is rising too fast. When this occurs the HD led remains locked on.

I can only conclude something is really wrong here, either with something in gnome or the kernel. I guess ill try burning from a terminal directly with growisofs to find out. I'm really annoyed with making coasters.

The DVD burner is attached slave in the second ide (hdd), the main system HD is in the same channel, i know this is suboptimal but the other 2 are occupied with more harddisks. And it used to work fine in Edgy Beta, the last time i burned many discs. Burner is Benq DW1620.

---

### Post by scoon on 2006-12-08
Hey there, 

When it worked, did you keep track of what modules got loaded?  Maybe not all the modules that used to get loaded are getting loaded now. Also, did the kernel change from beta to release?

-scoon

---

### Post by Artemis3 on 2006-12-08
Ah forget about it. When running growisofs i discovered errors like:

"timout waiting for dma" "drive not ready for command" "unable to write input/outpur error". With its resulting coaster... Back to windows and nero.

Or maybe i'll find something hdparm can help me with, hopefully.

---

### Post by scoon on 2006-12-08
Does dmesg say anything as growisofs gives those errors?

-scoon

---

### Post by Artemis3 on 2006-12-12
The same errors. Also things like these appear in the logs:

```
Dec  8 11:19:32 artemis3-desktop kernel: [17179925.548000] cdrom: This disc doesn't have any tracks I recognize!
Dec  8 11:34:49 artemis3-desktop -- MARK --
Dec  8 11:46:43 artemis3-desktop kernel: [17181556.208000] cdrom: This disc doesn't have any tracks I recognize!
Dec  8 11:53:40 artemis3-desktop kernel: [17181973.644000] hdd: DMA timeout retry
Dec  8 11:53:46 artemis3-desktop kernel: [17181978.900000] hdd: status timeout: status=0x90 { Busy }
Dec  8 11:53:46 artemis3-desktop kernel: [17181978.900000] ide: failed opcode was: unknown
Dec  8 11:53:46 artemis3-desktop kernel: [17181979.332000] hdd: ATAPI reset complete
Dec  8 11:53:46 artemis3-desktop kernel: [17181979.652000] hdd: status error: status=0x58 { DriveReady SeekComplete DataRequest }
Dec  8 11:53:46 artemis3-desktop kernel: [17181979.652000] ide: failed opcode was: unknown
Dec  8 11:55:28 artemis3-desktop kernel: [17182081.544000] cdrom: This disc doesn't have any tracks I recognize!
Dec  8 12:11:52 artemis3-desktop kernel: [17183065.400000] hdd: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
Dec  8 12:11:57 artemis3-desktop kernel: [17183065.400000] hdd: media error (bad sector): error=0x34 { AbortedCommand LastFailedSense=0x03 }
Dec  8 12:11:57 artemis3-desktop kernel: [17183065.400000] ide: failed opcode was: unknown
Dec  8 12:11:57 artemis3-desktop kernel: [17183065.400000] end_request: I/O error, dev hdd, sector 64
Dec  8 12:11:57 artemis3-desktop kernel: [17183070.480000] hdd: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
Dec  8 12:11:57 artemis3-desktop kernel: [17183070.480000] hdd: media error (bad sector): error=0x34 { AbortedCommand LastFailedSense=0x03 }
Dec  8 12:11:57 artemis3-desktop kernel: [17183070.480000] ide: failed opcode was: unknown
Dec  8 12:11:57 artemis3-desktop kernel: [17183070.480000] end_request: I/O error, dev hdd, sector 64
Dec  8 12:21:01 artemis3-desktop kernel: [17183614.280000] hdd: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
Dec  8 12:21:01 artemis3-desktop kernel: [17183614.280000] hdd: media error (bad sector): error=0x34 { AbortedCommand LastFailedSense=0x03 }
Dec  8 12:21:01 artemis3-desktop kernel: [17183614.280000] ide: failed opcode was: unknown
Dec  8 12:21:01 artemis3-desktop kernel: [17183614.280000] end_request: I/O error, dev hdd, sector 64
Dec  8 12:21:01 artemis3-desktop kernel: [17183614.280000] isofs_fill_super: bread failed, dev=hdd, iso_blknum=16, block=16
```

---

### Post by _simon_ on 2006-12-12
Have you tried k3b?

I was making coasters with gnomebaker and nero for linux. k3b works first time every time for me with both CD's and DVD's.

---

### Post by scoon on 2006-12-12
Hey there, 

Looks like DMA and that drive is unhappy.  Maybe tweak those settings w/ hdparm.  Possibly start with turning dma off.

-scoon

---

### Post by Artemis3 on 2006-12-12
I moved the hard drive to the other IDE cable and the errors (and coasters) stopped. DMA remains enabled by default now, no need for the /etc/hdparm.conf entry anymore.

Now it simply takes too long to burn (60mins with graveman, 30mins with brasero). Maybe a drive (firmware) or media (bad batch) issue...

---

