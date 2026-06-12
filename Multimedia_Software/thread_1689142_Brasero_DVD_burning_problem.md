---
title: "Brasero DVD burning problem"
date: 2011-02-16
forum: Multimedia Software
---

### Post by the_blue_box on 2011-02-16
Hi
 I've encountered a problem when trying to burn a video file to DVD using Brasero Disc Burner.
 I put the DVD and then open up Brasero and click on &#8220;video protect&#8221; then I chose the video file I want to burn, I click the &#8220;burn&#8221; button and choose the settings I want then when press the &#8220;burn&#8221; button once more. I then get this screen...
[IMG]http://i1085.photobucket.com/albums/j436/seajaydesigns/Screenshot-1.png[/IMG]

It then ejects the DVD and I get this...
[IMG]http://i1085.photobucket.com/albums/j436/seajaydesigns/Screenshot-UntitledWindow.png[/IMG]

any help would be much appreciated  :D
[COLOR=Blue]
the_blue_box[/COLOR]

---

### Post by An Sanct on 2011-02-16
How about saving the log and posting it here?

(as a "code" section or an attachment)

---

### Post by the_blue_box on 2011-02-16
Here you go
```
Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1741)
Unsupported type of task operation
Session error : An internal error occurred (brasero_burn_record brasero-burn.c:2839)
```

---

### Post by An Sanct on 2011-02-16
> **the_blue_box said:**
> Here you go
```
Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1741)
Unsupported type of task operation
Session error : An internal error occurred (brasero_burn_record brasero-burn.c:2839)
```

wow =)

I'm reading this as "don't use brasero for this kind of task"...

I use K3B, take a look, if you want. Its in the repositories.

---

### Post by oryan_dunn on 2011-04-01
I have the exact same behavior (even the log is the same).  Wonder what the problem could be?  Would be nice to have a more descriptive error message.  I'm using 10.04 and brasero 2.30.2

---

### Post by the_blue_box on 2011-04-18
That's interesting :-k . 

In the end I just gave up but I would still like to get to the bottom of it.

[COLOR=Blue]
the_blue_box[/COLOR]

---

### Post by hydrox24 on 2011-06-18
I also have this issue and it is more than irritating. I have tried using every combination of formats and burning speed and types of cds (rewritable and not). I think that it is important that we get to the bottom of this as there are TONS of posts and they all just hit dead ends. Time to change that!
My Error log is as follows:
```

BraseroVcdImager stdout: #write[3/3]: 44431/45095 (99%)          
BraseroVcdImager stdout: #write[3/3]: 44506/45095 (99%)          
BraseroVcdImager stdout: #write[3/3]: 44581/45095 (99%)          
BraseroVcdImager stdout: #write[3/3]: 44656/45095 (99%)          
BraseroVcdImager stdout: #write[3/3]: 44731/45095 (99%)          
BraseroVcdImager stdout: #write[3/3]: 44806/45095 (99%)          
BraseroVcdImager stdout: #write[3/3]: 44881/45095 (100%)          
BraseroVcdImager stdout: #write[3/3]: 44956/45095 (100%)          
BraseroVcdImager stdout: #write[3/3]: 45031/45095 (100%)          
BraseroVcdImager stdout: #write[3/3]: 45106/45095 (100%)          
BraseroVcdImager stdout: #write[3/3]: 45181/45095 (100%)          
BraseroVcdImager stderr: HUP
BraseroVcdImager stdout: #write[3/3]: 45245/45095 (100%)          
BraseroVcdImager stdout: HUP
BraseroVcdImager process finished with status 0
BraseroVcdImager Finished successfully session
BraseroVcdImager stopping
BraseroVcdImager called brasero_job_get_done_tracks
BraseroVcdImager called brasero_job_get_fd_out
BraseroVcdImager called brasero_job_get_action
BraseroVcdImager called brasero_job_get_output_type
BraseroVcdImager Automatically adding track
BraseroVcdImager called brasero_job_get_image_output
BraseroVcdImager called brasero_job_get_session_output_size
BraseroVcdImager called brasero_job_add_track
BraseroVcdImager called brasero_job_get_action
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
	speed=48
	driveropts=burnfree
	-dao
	fs=16m
	-text
	cuefile=/tmp/brasero_tmp_8UW4WV.cue
BraseroWodim Launching command in /tmp
BraseroWodim called brasero_job_get_fd_out
BraseroWodim called brasero_job_get_fd_in
BraseroWodim called brasero_job_get_fd_out
BraseroWodim stderr: wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: scsidev: '/dev/sr0'
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: devname: '/dev/sr0'
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: scsibus: -2 target: -2 lun: -2
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Linux sg driver version: 3.5.27
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Wodim version: 1.1.10
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
BraseroWodim stdout: Vendor_info    : 'HL-DT-ST'
BraseroWodim stdout: Identification : 'DVDRAM GH22NS50 '
BraseroWodim stdout: Revision       : 'TN01'
BraseroWodim stdout: Device seems to be: Generic mmc2 DVD-R/DVD-RW.
BraseroWodim stdout: Current: 0x0009 (CD-R)
BraseroWodim stdout: Profile: 0x0012 (DVD-RAM) 
BraseroWodim stdout: Profile: 0x0011 (DVD-R sequential recording) 
BraseroWodim stdout: Profile: 0x0015 (DVD-R/DL sequential recording) 
BraseroWodim stdout: Profile: 0x0016 (DVD-R/DL layer jump recording) 
BraseroWodim stdout: Profile: 0x0014 (DVD-RW sequential recording) 
BraseroWodim stdout: Profile: 0x0013 (DVD-RW restricted overwrite) 
BraseroWodim stdout: Profile: 0x001A (DVD+RW) 
BraseroWodim stdout: Profile: 0x001B (DVD+R) 
BraseroWodim stdout: Profile: 0x002B (DVD+R/DL) 
BraseroWodim stdout: Profile: 0x0010 (DVD-ROM) 
BraseroWodim stdout: Profile: 0x0009 (CD-R) (current)
BraseroWodim stdout: Profile: 0x000A (CD-RW) 
BraseroWodim stdout: Profile: 0x0008 (CD-ROM) 
BraseroWodim stdout: Profile: 0x0002 (Removable disk) 
BraseroWodim stdout: Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
BraseroWodim stdout: Driver flags   : MMC-3 SWABAUDIO BURNFREE 
BraseroWodim stdout: Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R96R
BraseroWodim stdout: Drive buf size : 1053696 = 1029 KB
BraseroWodim stdout: Drive DMA Speed: 16669 kB/s 94x CD 12x DVD
BraseroWodim stdout: FIFO size      : 16777216 = 16384 KB
BraseroWodim stderr: Speed set to 8468 KB/s
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Track 01: data     1 MB        
BraseroWodim stdout: Track 02: data    19 MB        
BraseroWodim stdout: Track 03: data    81 MB        
BraseroWodim stdout: Total size:      101 MB (10:03.26) = 45245 sectors
BraseroWodim stdout: Lout start:      101 MB (10:05/20) = 45245 sectors
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
BraseroWodim stdout: Blocks total: 359846 Blocks current: 359846 Blocks remaining: 314601
BraseroWodim stdout: Starting to write CD/DVD at speed  48.0 in real SAO mode for single session.
BraseroWodim stdout: Last chance to quit, starting real write in    4 seconds.
BraseroWodim called brasero_job_set_dangerous
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout:    3 seconds.
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout:    2 seconds.
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout:    1 seconds.   0 seconds. Operation starts.
BraseroWodim stdout: Waiting for reader process to fill input buffer ... input buffer ready.
BraseroWodim stdout: Performing OPC...
BraseroWodim stdout: Sending CUE sheet...
BraseroWodim called brasero_job_get_input_type
BraseroWodim called brasero_job_set_current_action
BraseroWodim stderr: Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: CDB:  2A 00 FF FF D2 8E 00 02 A0 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: SAO startsec: -11634
BraseroWodim stderr: status: 0x2 (CHECK CONDITION)
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Writing lead-in...
BraseroWodim stderr: Sense Bytes: 70 00 05 00 00 00 00 0A 2A 20 03 80 21 00 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: write CD-Text data: error after 0 bytes
BraseroWodim stderr: Sense Key: 0x5 Illegal Request, Segment 0
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Writing  time:    0.054s
BraseroWodim stderr: Sense Code: 0x21 Qual 0x00 (logical block address out of range) Fru 0x0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense flags: Blk 0 (not valid) 
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: cmd finished after 0.002s timeout 200s
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Could not write Lead-in.
BraseroWodim called brasero_job_get_flags
BraseroWodim called brasero_job_error
BraseroWodim finished with an error
BraseroWodim asked to stop because of an error
	error		= 15
	message	= "An error occured while writing to disc"
BraseroWodim stopping
BraseroWodim got killed
Session error : An error occured while writing to disc (brasero_burn_record brasero-burn.c:2839)

```
Please, if anyone has the time and energy, this issue needs to be fixed, or at-least explained!

---

