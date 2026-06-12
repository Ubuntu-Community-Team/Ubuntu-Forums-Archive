---
title: "CD burning - can't even SIMULATE"
date: 2008-06-08
forum: Multimedia Software
---

### Post by alexforcefive on 2008-06-08
Hey guys, so I'm trying to burn an iso and I keep making coasters. I've tried burning at the lowest speed and it still fails. I tried burning a test cd with a small file on it, to make sure the iso wasn't just too big. When I did this I decided to simulate the burning first - but even THAT failed! See screenshot :D

Here's the brasero log too:

```
Checking session consistency (brasero_burn_check_session_consistency burn.c:1714)
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no foreign URIs
BraseroLocalTrack stopping
BraseroMd5sumFile called brasero_job_get_output_type
BraseroMd5sumFile called brasero_job_get_current_track
BraseroMd5sumFile called brasero_job_get_action
BraseroMd5sumFile called brasero_job_get_action
BraseroMd5sumFile deactivating
BraseroMd5sumFile called brasero_job_get_output_type
BraseroMd5sumFile called brasero_job_get_current_track
BraseroMd5sumFile called brasero_job_get_action
BraseroMd5sumFile called brasero_job_get_action
BraseroMd5sumFile called brasero_job_get_action
BraseroMd5sumFile called brasero_job_get_input_type
BraseroMd5sumFile called brasero_job_get_current_track
BraseroMd5sumFile called brasero_job_set_current_action
BraseroMd5sumFile called brasero_job_set_progress
BraseroMd5sumFile called brasero_job_get_action
BraseroMd5sumFile called brasero_job_get_input_type
BraseroMd5sumFile called brasero_job_get_current_track
BraseroMd5sumFile called brasero_job_add_track
BraseroMd5sumFile called brasero_job_get_action
BraseroMd5sumFile finished track successfully
BraseroMd5sumFile stopping
BraseroWodim called brasero_job_get_action
BraseroWodim creating input
BraseroWodim getting varg
BraseroWodim called brasero_job_get_action
BraseroWodim got varg:
BraseroWodim deactivating
BraseroMd5sum called brasero_job_get_action
BraseroMd5sum creating input
BraseroMd5sum called brasero_job_get_action
BraseroMd5sum deactivating
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage getting varg
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_get_current_track
BraseroGenisoimage called brasero_job_get_tmp_dir
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_set_current_action
BraseroGenisoimage called brasero_job_start_progress
BraseroGenisoimage got varg:
	/usr/bin/genisoimage
	-input-charset
	utf8
	-r
	-J
	-graft-points
	-D
	-path-list
	/tmp/brasero_tmp_3I9ACU
	-exclude-list
	/tmp/brasero_tmp_OI9ACU
	-quiet
	-print-size
BraseroGenisoimage launching command
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage stderr: HUP
BraseroGenisoimage stdout: 89784
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_set_output_size_for_current_track
BraseroGenisoimage stdout: HUP
BraseroGenisoimage process finished with status 0
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage finished track successfully
BraseroGenisoimage got killed
BraseroGenisoimage stopping
BraseroWodim called brasero_job_get_action
BraseroWodim creating input
BraseroWodim getting varg
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_get_device
BraseroWodim called brasero_job_get_flags
BraseroWodim called brasero_job_get_speed
BraseroWodim called brasero_job_get_flags
BraseroWodim called brasero_job_get_input_type
BraseroWodim called brasero_job_get_fd_in
BraseroWodim called brasero_job_get_input_type
BraseroWodim called brasero_job_get_session_output_size
BraseroWodim called brasero_job_set_current_action
BraseroWodim got varg:
	wodim
	-v
	dev=/dev/scd0
	-dummy
	gracetime=0
	speed=56
	driveropts=burnfree
	-multi
	fs=8m
	tsize=89784s
	-dao
	-data
	-nopad
	-
BraseroWodim launching command
BraseroWodim called brasero_job_get_fd_out
BraseroMd5sum called brasero_job_get_action
BraseroMd5sum linked to BraseroWodim
BraseroMd5sum creating input
BraseroMd5sum called brasero_job_get_action
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage linked to BraseroMd5sum
BraseroGenisoimage getting varg
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_get_current_track
BraseroGenisoimage called brasero_job_get_tmp_dir
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_get_data_label
BraseroGenisoimage called brasero_job_get_flags
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage called brasero_job_set_current_action
BraseroGenisoimage got varg:
	/usr/bin/genisoimage
	-input-charset
	utf8
	-r
	-J
	-graft-points
	-D
	-path-list
	/tmp/brasero_tmp_8XOZBU
	-exclude-list
	/tmp/brasero_tmp_BWOZBU
	-V
	Data disc (09 Jun 08)
	-A
	Brasero-0.7.1
	-sysid
	LINUX
BraseroGenisoimage launching command
BraseroGenisoimage called brasero_job_get_fd_out
BraseroMd5sum called brasero_job_get_action
BraseroMd5sum called brasero_job_get_input_type
BraseroMd5sum called brasero_job_get_fd_in
BraseroMd5sum starting md5 generation live
BraseroMd5sum called brasero_job_set_nonblocking
BraseroMd5sum called brasero_job_get_fd_in
BraseroMd5sum called brasero_job_get_fd_out
BraseroMd5sum called brasero_job_get_fd_in
BraseroMd5sum called brasero_job_get_fd_out
BraseroWodim stderr: wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/scd0'
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: devname: '/dev/scd0'
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: scsibus: -2 target: -2 lun: -2
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Linux sg driver version: 3.5.27
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Wodim version: 1.1.6
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
BraseroWodim stdout: Vendor_info    : 'SONY    '
BraseroWodim stdout: Identification : 'DVD RW AW-G170A '
BraseroWodim stdout: Revision       : '1.71'
BraseroWodim stdout: Device seems to be: Generic mmc2 DVD-R/DVD-RW.
BraseroWodim stdout: Current: 0x0009 (CD-R)
BraseroWodim stdout: Profile: 0x002B (DVD+R/DL) 
BraseroWodim stdout: Profile: 0x001B (DVD+R) 
BraseroWodim stdout: Profile: 0x001A (DVD+RW) 
BraseroWodim stdout: Profile: 0x0016 (DVD-R/DL layer jump recording) 
BraseroWodim stdout: Profile: 0x0015 (DVD-R/DL sequential recording) 
BraseroWodim stdout: Profile: 0x0014 (DVD-RW sequential recording) 
BraseroWodim stdout: Profile: 0x0013 (DVD-RW restricted overwrite) 
BraseroWodim stdout: Profile: 0x0012 (DVD-RAM) 
BraseroWodim stdout: Profile: 0x0011 (DVD-R sequential recording) 
BraseroWodim stdout: Profile: 0x0010 (DVD-ROM) 
BraseroWodim stdout: Profile: 0x000A (CD-RW) 
BraseroWodim stdout: Profile: 0x0009 (CD-R) (current)
BraseroWodim stdout: Profile: 0x0008 (CD-ROM) (current)
BraseroWodim stdout: Profile: 0x0002 (Removable disk) 
BraseroWodim stdout: Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
BraseroWodim stdout: Driver flags   : MMC-3 SWABAUDIO BURNFREE 
BraseroWodim stdout: Supported modes: TAO PACKET SAO SAO/R96R RAW/R96R
BraseroWodim stdout: Drive buf size : 890880 = 870 KB
BraseroWodim stdout: FIFO size      : 8388608 = 8192 KB
BraseroWodim stderr: Speed set to 8467 KB/s
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Track 01: data   175 MB        
BraseroWodim stdout: Total size:      201 MB (19:57.12) = 89784 sectors
BraseroWodim stdout: Lout start:      201 MB (19:59/09) = 89784 sectors
BraseroWodim stdout: Current Secsize: 2048
BraseroWodim stdout: ATIP info from disk:
BraseroWodim stdout:   Indicated writing power: 4
BraseroWodim stdout:   Is not unrestricted
BraseroWodim stdout:   Is not erasable
BraseroWodim stdout:   Disk sub type: Medium Type A, low Beta category (A-) (2)
BraseroWodim stdout:   ATIP start of lead in:  -12508 (97:15/17)
BraseroWodim stdout:   ATIP start of lead out: 359845 (79:59/70)
BraseroWodim stdout: Disk type:    Short strategy type (Phthalocyanine or similar)
BraseroWodim stdout: Manuf. index: 22
BraseroWodim stdout: Manufacturer: Ritek Co.
BraseroWodim stdout: Blocks total: 359845 Blocks current: 359845 Blocks remaining: 270061
BraseroWodim stdout: Starting to write CD/DVD at speed  48.0 in dummy SAO mode for multi session.
BraseroWodim stdout: Last chance to quit, starting dummy write in  0 seconds. Operation starts.
BraseroWodim called brasero_job_set_dangerous
BraseroWodim stdout: Waiting for reader process to fill input buffer ... input buffer ready.
BraseroWodim stdout: Sending CUE sheet...
BraseroWodim called brasero_job_get_input_type
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Writing pregap for track 1 at -150
BraseroWodim stdout: Starting new track at sector: 0
BraseroWodim stdout: 
BraseroWodim stderr: Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: CDB:  2A 00 00 00 00 1F 00 00 1F 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: status: 0x2 (CHECK CONDITION)
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Bytes: 70 00 04 00 00 00 00 0A 00 00 00 00 08 03 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Key: 0x4 Hardware Error, Segment 0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Code: 0x08 Qual 0x03 (logical unit communication crc error (ultra-dma/32)) Fru 0x0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense flags: Blk 0 (not valid) 
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: cmd finished after 0.001s timeout 200s
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: A write error occured.
BraseroWodim called brasero_job_get_flags
BraseroWodim called brasero_job_error
BraseroWodim finished with an error
BraseroWodim asked to stop because of an error
	error		= 1
	message	= "a write error occured which was likely due to overburning the disc"
BraseroGenisoimage stopping
BraseroGenisoimage got killed
BraseroGenisoimage disconnecting BraseroGenisoimage from BraseroMd5sum
BraseroMd5sum stopping
BraseroMd5sum disconnecting BraseroMd5sum from BraseroWodim
BraseroMd5sum closing connection for BraseroMd5sum
BraseroWodim stopping
BraseroWodim got killed
BraseroWodim stderr: wodim: Please properly read the error message above.
BraseroWodim called brasero_job_get_flags
BraseroWodim closing connection for BraseroWodim
Session error : a write error occured which was likely due to overburning the disc (brasero_burn_record burn.c:2270)
```

If anyone can help me figure this out, I'd really appreciate it. Thanks!

---

### Post by ales on 2008-07-05
Hi,

I have same problem and same error.
But before it worked. Maybe some updates changed something in Ubuntu.
Looking for solution too.

Ales

---

### Post by Lawrence Talbot on 2008-07-06
I would switch to K3b, I just think it works better.

---

### Post by tombo465 on 2008-07-06
if k3b doesn't work either try gnomebaker . I had problems to when i started . I found that tovid works the best for videos and gnomebaker for audio on my machine. oh!  be shure when you install any of these programs click yes on any of the support programs synaptic tells you to install.  hope you figure it out ! it can get frustating.

---

