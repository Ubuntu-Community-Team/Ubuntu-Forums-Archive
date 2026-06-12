---
title: "DVD burn error"
date: 2010-06-16
forum: Multimedia Software
---

### Post by MrChainBlueLightnin on 2010-06-16
I have ubuntu 9.04 and am using DeVeDe to create the iso and brasero discburn to burn a dvd movie.  I keep getting this error log:

                                 Checking session consistency (brasero_burn_check_session_consistency burn.c:1905)  
 BraseroBurnURI called brasero_job_get_action  
 BraseroBurnURI called brasero_job_get_action  
 BraseroBurnURI called brasero_job_set_output_size_for_current_track  
 BraseroBurnURI stopping  
 BraseroBurnURI called brasero_job_get_action  
 BraseroBurnURI called brasero_job_get_session_output_size  
 BraseroBurnURI output set (IMAGE) image = /tmp/brasero_tmp_A1D8DV.bin toc = none  
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
 BraseroLocalTrack output set (IMAGE) image = /tmp/brasero_tmp_XHT8DV.bin toc = none  
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
 BraseroChecksumImage output set (IMAGE) image = /tmp/brasero_tmp_P8W8DV.bin toc = none  
 BraseroChecksumImage called brasero_job_get_action  
 BraseroChecksumImage called brasero_job_get_action  
 BraseroChecksumImage called brasero_job_get_input_type  
 BraseroChecksumImage called brasero_job_set_current_action  
 BraseroChecksumImage called brasero_job_get_fd_in  
 BraseroChecksumImage called brasero_job_get_current_track  
 BraseroChecksumImage called brasero_job_get_current_track  
 BraseroChecksumImage Starting checksuming file /home/bloody/SRV Live at Montreux 1982/SRV Live at Montreux 1982.iso (size = -1644980224)  
 BraseroChecksumImage called brasero_job_get_fd_out  
 BraseroChecksumImage called brasero_job_get_current_track  
 BraseroChecksumImage Setting new checksum (type = 2) 91b5f096b04f52356191cf17626a8e32 ( before)  
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
     /home/bloody/SRV Live at Montreux 1982/SRV Live at Montreux 1982.iso  
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
 BraseroWodim stdout: TOC Type: 1 = CD-ROM  
 BraseroWodim stderr: communication breaks or freezes immediately after that.  
 BraseroWodim called brasero_job_get_flags  
 BraseroWodim stdout: Driveropts: 'burnfree'  
 BraseroWodim stderr: Speed set to 11080 KB/s  
 BraseroWodim called brasero_job_get_flags  
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
 BraseroWodim stdout: Track 01: data  2527 MB         
 BraseroWodim stdout: Total size:     2902 MB (287:32.52) = 1293939 sectors  
 BraseroWodim stdout: Lout start:     2902 MB (287:34/39) = 1293939 sectors  
 BraseroWodim stdout: Current Secsize: 2048  
 BraseroWodim stdout: HINT: use dvd+rw-mediainfo from dvd+rw-tools for information extraction.  
 BraseroWodim stdout: Blocks total: 2298496 Blocks current: 2298496 Blocks remaining: 1004557  
 BraseroWodim stdout: Starting to write CD/DVD at speed   8.0 in real SAO mode for single session.  
 BraseroWodim stdout: Last chance to quit, starting real write in    4 seconds.#  
 BraseroWodim called brasero_job_set_dangerous  
 BraseroWodim stdout: #  
 BraseroWodim stdout: #  
 BraseroWodim stdout: #  
 BraseroWodim stdout: #  
 BraseroWodim stdout: #  
 BraseroWodim stdout: #  
 BraseroWodim stdout: #  
 BraseroWodim stdout: #  
 BraseroWodim stdout: #  
 BraseroWodim stdout: #  
 BraseroWodim stdout: #  
 BraseroWodim stdout: #  
 BraseroWodim stdout:    3 seconds.#  
 BraseroWodim stdout: #  
 BraseroWodim stdout: #  
 BraseroWodim stdout: #  
 BraseroWodim stdout: #  
 BraseroWodim stdout: #  
 BraseroWodim stdout: #  
 BraseroWodim stdout: #  
 BraseroWodim stdout: #  
 BraseroWodim stdout: #  
 BraseroWodim stdout: #  
 BraseroWodim stdout: #  
 BraseroWodim stdout: #  
 BraseroWodim stdout:    2 seconds.#  
 BraseroWodim stdout: #  
 BraseroWodim stdout: #  
 BraseroWodim stdout: #  
 BraseroWodim stdout: #  
 BraseroWodim stdout: #  
 BraseroWodim stdout: #  
 BraseroWodim stdout: #  
 BraseroWodim stdout: #  
 BraseroWodim stdout: #  
 BraseroWodim stdout: #  
 BraseroWodim stdout: #  
 BraseroWodim stdout: #  
 BraseroWodim stdout:    1 seconds.#############   0 seconds. Operation starts.  
 BraseroWodim stdout: Waiting for reader process to fill input buffer ... input buffer ready.  
 BraseroWodim stdout: Performing OPC...  
 BraseroWodim stdout: Sending CUE sheet...  
 BraseroWodim called brasero_job_get_input_type  
 BraseroWodim called brasero_job_set_current_action  
 BraseroWodim stdout: Starting new track at sector: 0  
 BraseroWodim stdout:  
 BraseroWodim stdout: Track 01:    0 of 2527 MB written.  
 BraseroWodim stdout: Track 01:    1 of 2527 MB written (fifo  95%) [buf  85%]   0.0x.  
 BraseroWodim called brasero_job_get_action  
 BraseroWodim called brasero_job_set_current_action  
 BraseroWodim stdout: Track 01:    2 of 2527 MB written (fifo 100%) [buf  99%]   1.3x.  
 BraseroWodim called brasero_job_get_action  
 BraseroWodim called brasero_job_set_current_action  
 BraseroWodim stdout: Track 01:    3 of 2527 MB written (fifo  99%) [buf  99%]   4.3x.  
 BraseroWodim called brasero_job_get_action  
 BraseroWodim called brasero_job_set_current_action  
 BraseroWodim stdout: Track 01:    4 of 2527 MB written (fifo 100%) [buf  99%]   4.1x.  
 BraseroWodim called brasero_job_get_action  
 BraseroWodim called brasero_job_set_current_action  
 BraseroWodim stdout: Track 01:    5 of 2527 MB written (fifo  97%) [buf  99%]   4.3x.  
 BraseroWodim called brasero_job_get_action  
 BraseroWodim called brasero_job_set_current_action  
 BraseroWodim stdout: Track 01:    6 of 2527 MB written (fifo  98%) [buf  99%]   4.1x.  
 BraseroWodim called brasero_job_get_action  
 BraseroWodim called brasero_job_set_current_action  
 BraseroWodim stdout: Track 01:    7 of 2527 MB written (fifo  97%) [buf  99%]   4.2x.  
 BraseroWodim called brasero_job_get_action  
 BraseroWodim called brasero_job_set_current_action  
 BraseroWodim stdout: Track 01:    8 of 2527 MB written (fifo 100%) [buf  99%]   4.1x.  
 BraseroWodim called brasero_job_get_action  
 BraseroWodim called brasero_job_set_current_action  
 BraseroWodim stdout: Track 01:    9 of 2527 MB written (fifo  99%) [buf  99%]   4.2x.  
 BraseroWodim called brasero_job_get_action  
 BraseroWodim called brasero_job_set_current_action  
 BraseroWodim stdout: Track 01:   10 of 2527 MB written (fifo 100%) [buf  98%]   4.1x.  
 BraseroWodim called brasero_job_get_action  
 BraseroWodim called brasero_job_set_current_action  
 BraseroWodim stdout: Track 01:   11 of 2527 MB written (fifo  99%) [buf  99%]   4.3x.  
 BraseroWodim called brasero_job_get_action  
 BraseroWodim called brasero_job_set_current_action  
 BraseroWodim stdout: Track 01:   12 of 2527 MB written (fifo 100%) [buf  99%]   4.1x.  
 BraseroWodim called brasero_job_get_action  
 BraseroWodim called brasero_job_set_current_action  
 BraseroWodim stdout: Track 01:   13 of 2527 MB written (fifo  99%) [buf  99%]   4.3x.  
 BraseroWodim called brasero_job_get_action  
 BraseroWodim called brasero_job_set_current_action  
 BraseroWodim stdout: Track 01:   14 of 2527 MB written (fifo  99%) [buf  99%]   4.1x.  
 BraseroWodim called brasero_job_get_action  
 BraseroWodim called brasero_job_set_current_action  
 BraseroWodim stdout: Track 01:   15 of 2527 MB written (fifo  99%) [buf  99%]   4.2x.  
 BraseroWodim called brasero_job_get_action  
 BraseroWodim called brasero_job_set_current_action  
 BraseroWodim stdout: Track 01:   16 of 2527 MB written (fifo 100%) [buf  98%]   4.0x.  
 BraseroWodim called brasero_job_get_action  
 BraseroWodim called brasero_job_set_current_action  
 BraseroWodim stderr: Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error  
 BraseroWodim called brasero_job_get_flags  
 BraseroWodim stderr: CDB:  2A 00 00 00 22 83 00 00 1F 00  
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
 BraseroWodim stderr: cmd finished after 30.135s timeout 200s  
 BraseroWodim called brasero_job_get_flags  
 BraseroWodim stderr: wodim: A write error occured.  
 BraseroWodim called brasero_job_get_flags  
 BraseroWodim stderr: wodim: Please properly read the error message above.  
 BraseroWodim called brasero_job_get_flags  
 BraseroWodim stderr: Errno: 5 (Input/output error), test unit ready scsi sendcmd: no error  
 BraseroWodim called brasero_job_get_flags  
 BraseroWodim stdout: Track 01:   17 of 2527 MB written (fifo  99%) [buf  99%]   4.3x.  
 BraseroWodim called brasero_job_get_action  
 BraseroWodim called brasero_job_set_current_action  
 BraseroWodim stderr: CDB:  00 00 00 00 00 00  
 BraseroWodim called brasero_job_get_flags  
 BraseroWodim stdout: write track data: error after 18094080 bytes  
 BraseroWodim stderr: status: 0x2 (CHECK CONDITION)  
 BraseroWodim called brasero_job_get_flags  
 BraseroWodim stdout: Writing  time:   86.939s  
 BraseroWodim stderr: Sense Bytes: 70 00 02 00 00 00 00 0A 00 00 00 00 04 01 00 00  
 BraseroWodim called brasero_job_get_flags  
 BraseroWodim stdout: Average write speed  30.9x.  
 BraseroWodim stderr: Sense Key: 0x2 Not Ready, Segment 0  
 BraseroWodim called brasero_job_get_flags  
 BraseroWodim stdout: Min drive buffer fill was 98%  
 BraseroWodim stderr: Sense Code: 0x04 Qual 0x01 (logical unit is in process of becoming ready) Fru 0x0  
 BraseroWodim called brasero_job_get_flags  
 BraseroWodim stdout: Fixating...  
 BraseroWodim called brasero_job_set_current_action  
 BraseroWodim stderr: Sense flags: Blk 0 (not valid)  
 BraseroWodim called brasero_job_get_flags  
 BraseroWodim stderr: cmd finished after 0.418s timeout 200s  
 BraseroWodim called brasero_job_get_flags  
 BraseroWodim stderr: Errno: 5 (Input/output error), flush cache scsi sendcmd: no error  
 BraseroWodim called brasero_job_get_flags  
 BraseroWodim stdout: Trouble flushing the cache  
 BraseroWodim stderr: CDB:  35 00 00 00 00 00 00 00 00 00  
 BraseroWodim called brasero_job_get_flags  
 BraseroWodim stdout: Fixating time:    0.641s  
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
 BraseroWodim stderr: cmd finished after 0.640s timeout 200s  
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

### Post by alphacrucis2 on 2010-06-16
Try installing k3b. That seems to work better than brasero for me.

---

### Post by MrChainBlueLightnin on 2010-06-16
when i go to dvd drive properties it says  it is not mounted.  did you have to manually mount the drive?

---

### Post by sidzen on 2010-06-16
Yeh, or simply burn with the CLI and the <wodim> command!

I want SRV Live at Montreux 1982/SRV Live at Montreux 1982.iso !!!!

[PHP]wodim -sao speed=4 SRV_Live_at_Montreux-1982.iso [/PHP]You may have to rename the ISO without spaces, though, like I did above.

If this doesn't work, either, you have conflicts, most likely.  They can be worked out, too.

Get back with details, fellow SRV freak.:guitar:

---

