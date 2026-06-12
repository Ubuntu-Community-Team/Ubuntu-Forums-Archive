---
title: "Cannot Burn DVDs from ISO with Brasero"
date: 2009-12-02
forum: Multimedia Software
---

### Post by fattom23 on 2009-12-02
Since upgrading to 64 Bit Karmic, I can't burn DVDs anymore with Brasero and the Write to Disc command.  Brasero just quits near the end of the write process with this output:
```
Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1848)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI output set (IMAGE) image = /tmp/brasero_tmp_MH8G4U.bin toc = none
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI no burn:// URI found
BraseroBurnURI stopping
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs getting varg
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs got varg:
BraseroGrowisofs deactivating
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs getting varg
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_flags
BraseroGrowisofs called brasero_job_get_speed
BraseroGrowisofs called brasero_job_get_device
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_session_output_size
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_get_fd_in
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs got varg:
	growisofs
	-use-the-force-luke=notray
	-use-the-force-luke=4gms
	-dvd-compat
	-speed=16
	-use-the-force-luke=tracksize:1156357
	-use-the-force-luke=tty
	-Z
	/dev/sr0=/home/fattom/Downloads/scrooged/scrooged.iso
BraseroGrowisofs Launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stdout: Executing 'builtin_dd if=/home/fattom/Downloads/scrooged/scrooged.iso of=/dev/sr0 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
BraseroGrowisofs stderr: /dev/sr0: "Current Write Speed" is 16.4x1352KBps.
BraseroGrowisofs stdout:     1015808/2368219136 ( 0.0%) @0.0x, remaining 194:11 RBU  99.5% UBU   6.2%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:     1015808/2368219136 ( 0.0%) @0.0x, remaining 349:33 RBU  99.5% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:     1015808/2368219136 ( 0.0%) @0.0x, remaining 466:04 RBU  99.5% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:     1015808/2368219136 ( 0.0%) @0.0x, remaining 582:35 RBU  99.5% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:     1015808/2368219136 ( 0.0%) @0.0x, remaining 737:56 RBU  99.5% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:     1015808/2368219136 ( 0.0%) @0.0x, remaining 854:28 RBU  99.5% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:     1015808/2368219136 ( 0.0%) @0.0x, remaining 970:59 RBU  99.5% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:     1015808/2368219136 ( 0.0%) @0.0x, remaining 1126:20 RBU  99.5% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:     1015808/2368219136 ( 0.0%) @0.0x, remaining 1242:51 RBU  99.5% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:     1015808/2368219136 ( 0.0%) @0.0x, remaining 1359:22 RBU  99.5% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:     1015808/2368219136 ( 0.0%) @0.0x, remaining 1514:44 RBU  99.5% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:     1015808/2368219136 ( 0.0%) @0.0x, remaining 1631:15 RBU  99.5% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:     2555904/2368219136 ( 0.1%) @0.3x, remaining 694:10 RBU  95.9% UBU  59.4%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:     8880128/2368219136 ( 0.4%) @1.4x, remaining 216:58 RBU  91.1% UBU  56.2%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:     8880128/2368219136 ( 0.4%) @0.0x, remaining 230:15 RBU  91.1% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:     8880128/2368219136 ( 0.4%) @0.0x, remaining 243:32 RBU  91.1% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:     8880128/2368219136 ( 0.4%) @0.0x, remaining 261:15 RBU  91.1% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:     8880128/2368219136 ( 0.4%) @0.0x, remaining 274:32 RBU  91.1% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:     8880128/2368219136 ( 0.4%) @0.0x, remaining 287:49 RBU  91.1% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:     8880128/2368219136 ( 0.4%) @0.0x, remaining 305:32 RBU  91.1% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:     8880128/2368219136 ( 0.4%) @0.0x, remaining 318:49 RBU  91.1% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:     8880128/2368219136 ( 0.4%) @0.0x, remaining 332:06 RBU  91.1% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:     8880128/2368219136 ( 0.4%) @0.0x, remaining 349:49 RBU  91.1% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:     8880128/2368219136 ( 0.4%) @0.0x, remaining 363:06 RBU  91.1% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:     8880128/2368219136 ( 0.4%) @0.0x, remaining 376:23 RBU  91.1% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:     8880128/2368219136 ( 0.4%) @0.0x, remaining 394:06 RBU  91.1% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:     8880128/2368219136 ( 0.4%) @0.0x, remaining 407:23 RBU  91.1% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:     8880128/2368219136 ( 0.4%) @0.0x, remaining 420:40 RBU  91.1% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:     8880128/2368219136 ( 0.4%) @0.0x, remaining 438:23 RBU  91.1% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:     8880128/2368219136 ( 0.4%) @0.0x, remaining 451:40 RBU  91.1% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:     8880128/2368219136 ( 0.4%) @0.0x, remaining 464:57 RBU  91.1% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr: :-[ WRITE@LBA=10f0h failed with SK=0h/ASC=00h/ACQ=02h]: Input/output error
BraseroGrowisofs stdout:     8880128/2368219136 ( 0.4%) @0.0x, remaining 482:39 RBU  91.1% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr: :-( write failed: Input/output error
BraseroGrowisofs stdout:     8880128/2368219136 ( 0.4%) @0.0x, remaining 495:57 RBU  91.1% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr: /dev/sr0: flushing cache
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:     8880128/2368219136 ( 0.4%) @0.0x, remaining 509:14 RBU  91.1% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:     8880128/2368219136 ( 0.4%) @0.0x, remaining 526:56 RBU  91.1% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:     8880128/2368219136 ( 0.4%) @0.0x, remaining 540:13 RBU  91.1% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr: /dev/sr0: updating RMA
BraseroGrowisofs stderr: /dev/sr0: closing disc
BraseroGrowisofs stderr: HUP
BraseroGrowisofs stdout: HUP
BraseroGrowisofs process finished with status 5
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
	error		= 0
	message	= "no message"
BraseroGrowisofs stopping
BraseroGrowisofs got killed
Session error : unknown (brasero_burn_record brasero-burn.c:2811)
```

Since the upgrade, I've also been having a mount/unmount problem with that drive (described in [this thread]("http://ubuntuforums.org/showthread.php?t=1344106")), so they might be related.  Any ideas of things that I could try?

---

