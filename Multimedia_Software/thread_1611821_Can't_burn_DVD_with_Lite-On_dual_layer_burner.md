---
title: "Can't burn DVD with Lite-On dual layer burner"
date: 2010-11-02
forum: Multimedia Software
---

### Post by MrChainBlueLightnin on 2010-11-02
I am trying to burn a DVD-R.  It won't burn data or video iso or even make a copy.  It worked after a fresh install, but after my first security update it always corrupts the burner. I have a Lite-On Dual Layer burner model SOHW-1633S.  I have Ubuntu 9.04.  Here is the error log.

Checking session consistency (brasero_burn_check_session_consistency burn.c:1905)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI output set (IMAGE) image = /tmp/brasero_tmp_Z1ZOLV.bin toc = none
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI called brasero_job_get_input_type
BraseroBurnURI no burn:// URI found
BraseroBurnURI stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_set_output_size_for_current_track
BraseroLocalTrack stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack output set (IMAGE) image = /tmp/brasero_tmp_35EPLV.bin toc = none
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no remote URIs
BraseroLocalTrack stopping
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_flags
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_set_output_size_for_current_track
BraseroChecksumImage stopping
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_flags
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_session_output_size
BraseroChecksumImage output set (IMAGE) image = /tmp/brasero_tmp_HKIPLV.bin toc = none
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_input_type
BraseroChecksumImage called brasero_job_set_current_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage Starting checksuming file /home/administrator/Videos/movie/movie.iso (size = -1879939072)
BraseroChecksumImage called brasero_job_get_fd_out
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage Setting new checksum (type = 2) 0b4ed93a7e8a240016572854489f87df ( before)
BraseroChecksumImage Finished track successfully
BraseroChecksumImage stopping
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
    speed=8
    driveropts=burnfree
    -dao
    fs=16m
    -data
    -nopad
    /home/administrator/Videos/movie/movie.iso
BraseroWodim Launching command
BraseroWodim called brasero_job_get_fd_out
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
BraseroWodim stderr: Speed set to 11080 KB/s
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Driveropts: 'burnfree'
BraseroWodim stdout: Device type    : Removable CD-ROM
BraseroWodim stdout: Version        : 5
BraseroWodim stdout: Response Format: 2
BraseroWodim stdout: Capabilities   : 
BraseroWodim stdout: Vendor_info    : 'LITE-ON '
BraseroWodim stdout: Identification : 'DVDRW SOHW-1633S'
BraseroWodim stdout: Revision       : 'BS0Y'
BraseroWodim stdout: Device seems to be: Generic mmc2 DVD-R/DVD-RW.
BraseroWodim stdout: Current: 0x0011 (DVD-R sequential recording)
BraseroWodim stdout: Profile: 0x002B (DVD+R/DL) 
BraseroWodim stdout: Profile: 0x001B (DVD+R) 
BraseroWodim stdout: Profile: 0x001A (DVD+RW) 
BraseroWodim stdout: Profile: 0x0014 (DVD-RW sequential recording) 
BraseroWodim stdout: Profile: 0x0013 (DVD-RW restricted overwrite) 
BraseroWodim stdout: Profile: 0x0011 (DVD-R sequential recording) (current)
BraseroWodim stdout: Profile: 0x0010 (DVD-ROM) 
BraseroWodim stdout: Profile: 0x000A (CD-RW) 
BraseroWodim stdout: Profile: 0x0009 (CD-R) 
BraseroWodim stdout: Profile: 0x0008 (CD-ROM) 
BraseroWodim stdout: Using generic SCSI-3/mmc DVD-R(W) driver (mmc_mdvd).
BraseroWodim stdout: Driver flags   : SWABAUDIO BURNFREE 
BraseroWodim stdout: Supported modes: PACKET SAO
BraseroWodim stdout: Drive buf size : 1563904 = 1527 KB
BraseroWodim stdout: FIFO size      : 16777216 = 16384 KB
BraseroWodim stdout: Track 01: data  2303 MB        
BraseroWodim stdout: Total size:     2645 MB (262:02.84) = 1179213 sectors
BraseroWodim stdout: Lout start:     2645 MB (262:04/63) = 1179213 sectors
BraseroWodim stdout: Current Secsize: 2048
BraseroWodim stdout: HINT: use dvd+rw-mediainfo from dvd+rw-tools for information extraction.
BraseroWodim stdout: Blocks total: 2298496 Blocks current: 2298496 Blocks remaining: 1119283
BraseroWodim stdout: Starting to write CD/DVD at speed   8.0 in real SAO mode for single session.
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
BraseroWodim stdout: Starting new track at sector: 0
BraseroWodim stdout: 
BraseroWodim stdout: Track 01:    0 of 2303 MB written.
BraseroWodim stdout: Track 01:    1 of 2303 MB written (fifo  99%) [buf  85%]   0.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    2 of 2303 MB written (fifo 100%) [buf  99%]   1.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    3 of 2303 MB written (fifo  97%) [buf  99%]   4.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    4 of 2303 MB written (fifo  93%) [buf  99%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    5 of 2303 MB written (fifo  99%) [buf  99%]   4.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    6 of 2303 MB written (fifo 100%) [buf  99%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    7 of 2303 MB written (fifo  99%) [buf  99%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    8 of 2303 MB written (fifo 100%) [buf  98%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    9 of 2303 MB written (fifo  99%) [buf  99%]   4.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   10 of 2303 MB written (fifo  99%) [buf  99%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   11 of 2303 MB written (fifo  99%) [buf  99%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   12 of 2303 MB written (fifo  99%) [buf  99%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   13 of 2303 MB written (fifo  99%) [buf  99%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   14 of 2303 MB written (fifo  99%) [buf  99%]   4.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   15 of 2303 MB written (fifo  99%) [buf  99%]   4.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   16 of 2303 MB written (fifo 100%) [buf  98%]   4.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stderr: Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: CDB:  2A 00 00 00 22 E0 00 00 1F 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: status: 0x2 (CHECK CONDITION)
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Bytes: 70 00 02 00 00 00 00 0A 00 00 00 00 04 01 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Key: 0x2 Not Ready, Segment 0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Code: 0x04 Qual 0x01 (logical unit is in process of becoming ready) Fru 0x0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense flags: Blk 0 (not valid) 
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: cmd finished after 29.758s timeout 200s
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: A write error occured.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Please properly read the error message above.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Errno: 5 (Input/output error), test unit ready scsi sendcmd: no error
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Track 01:   17 of 2303 MB written (fifo  99%) [buf  98%]   4.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stderr: CDB:  00 00 00 00 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: write track data: error after 18284544 bytes
BraseroWodim stderr: status: 0x2 (CHECK CONDITION)
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Writing  time:   86.755s
BraseroWodim stderr: Sense Bytes: 70 00 02 00 00 00 00 0A 00 00 00 00 04 01 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Average write speed  28.5x.
BraseroWodim stderr: Sense Key: 0x2 Not Ready, Segment 0
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Min drive buffer fill was 98%
BraseroWodim stderr: Sense Code: 0x04 Qual 0x01 (logical unit is in process of becoming ready) Fru 0x0
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Fixating...
BraseroWodim called brasero_job_set_current_action
BraseroWodim stderr: Sense flags: Blk 0 (not valid) 
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: cmd finished after 0.397s timeout 200s
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Errno: 5 (Input/output error), flush cache scsi sendcmd: no error
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Trouble flushing the cache
BraseroWodim stderr: CDB:  35 00 00 00 00 00 00 00 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Fixating time:    0.639s
BraseroWodim stderr: status: 0x2 (CHECK CONDITION)
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Bytes: 70 00 02 00 00 00 00 0A 00 00 00 00 04 01 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Key: 0x2 Not Ready, Segment 0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Code: 0x04 Qual 0x01 (logical unit is in process of becoming ready) Fru 0x0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense flags: Blk 0 (not valid) 
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: cmd finished after 0.639s timeout 200s
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Cannot fixate disk.
BraseroWodim called brasero_job_get_flags
BraseroWodim called brasero_job_error
BraseroWodim finished with an error
BraseroWodim asked to stop because of an error
    error        = 12
    message    = "An error occured while writing to disc"
BraseroWodim stopping
BraseroWodim got killed
Session error : An error occured while writing to disc (brasero_burn_record burn.c:2599)

---

### Post by ezsit on 2010-11-02
I have given up on Brasero and installed Gnomebaker. Brasero has corrupted the last eight CD and DVD data discs I have tried under 10.10. Before Maverick, Brasero worked just fine, now it is garbage.

---

### Post by Jay Car on 2010-11-02
> **ezsit said:**
> I have given up on Brasero and installed Gnomebaker. Brasero has corrupted the last eight CD and DVD data discs I have tried under 10.10. Before Maverick, Brasero worked just fine, now it is garbage.

I agree about Brasero, it's just unreliable, in my experience. But, for me, it started long before Maverick. I really like K3b.  It's easy and works great. Better than my old Nero.  

I've never used Gnomebaker. I'll try it out.

---

### Post by tommcd on 2010-11-02
Here is another vote for using Gnomebaker. I have always found Gnomebaker to be more reliable than Brasero.
Also, try burning the DVDs at the slowest possible speed. It (obviously) takes longer, but your DVDs are less likely to be corrupted.

---

### Post by heavy metal on 2010-11-03
I don't understand... I'm using brasero to burn dvd's and audio cd's and it just works fine in ubuntu 10.04.1, I'm thinking it's something to do with the hardware you have, my burner is a lite-on dvd-writer model ihas-324a sata.

---

### Post by MrChainBlueLightnin on 2010-11-03
It has absolutely nothing to do with hardware.  Conf. is the problem.  It seems to be a problem that none of the mods address.  Most of the posts say solved because the starter finally gave up.

---

