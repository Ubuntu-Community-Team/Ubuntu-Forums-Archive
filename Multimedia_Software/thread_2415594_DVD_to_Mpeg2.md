---
title: "DVD to Mpeg2"
date: 2019-03-28
forum: Multimedia Software
---

### Post by mlempenau on 2019-03-28
I'm using Ubuntu 18.04 and want to rip a Karaoke DVD and make a VCD for use on an old player.  I have tried ripping with Handbrake using the Mpeg2 setting.  Then I have tried to burn using K3b and DeVeDe and in both cases I get an instant error message.  So then I tried ripping using VLC media player again using a Mpeg2 setting.  I got the same results when I wanted to burn it using K3b or DeVeDe.  I would appreciate some suggestions on what I should do next.  

Error results from DeVeDe:
```
Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1739)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI output set (IMAGE) image = /tmp/brasero_tmp_5AOCZZ.bin toc = /tmp/brasero_tmp_5AOCZZ.cue
BraseroBurnURI called brasero_job_get_session_output_size
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
BraseroLocalTrack output set (IMAGE) image = /tmp/brasero_tmp_L2QCZZ.bin toc = /tmp/brasero_tmp_L2QCZZ.cue
BraseroLocalTrack called brasero_job_get_session_output_size
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
    speed=48
    driveropts=burnfree
    -dao
    fs=16m
    -text
    cuefile=/home/mlempenau/Copy/movie/movie.cue
BraseroWodim Launching command in /home/mlempenau/Copy/movie
BraseroWodim called brasero_job_get_fd_out
BraseroWodim called brasero_job_get_fd_in
BraseroWodim called brasero_job_get_fd_out
BraseroWodim stderr: wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Resource temporarily unavailable. Cannot get mmap for 16781312 Bytes on /dev/zero.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: TOC Type: 1 = CD-ROM
BraseroWodim stderr: HUP
BraseroWodim stdout: HUP
BraseroWodim process finished with status 11
BraseroWodim called brasero_job_error
BraseroWodim finished with an error
BraseroWodim asked to stop because of an error
    error        = 0
    message    = "no message"
BraseroWodim stopping
Session error : unknown (brasero_burn_record brasero-burn.c:2859)
```

---

### Post by lisati on 2019-03-28
I sometimes use Handbrake as part of a process of re-authoring DVDs I've previously made of camcorder footage. So far I have had useful results with both the m4v container and the mkv container, without recoding to mpeg2 within Handbrake - both devede and DVDStyler seem to cope well with .mkv files I've made on both Windows and (l)ubuntu.

---

### Post by mlempenau on 2019-03-29
Your advice was very good.  I was trying to do something unnecessary.  I  deleted the files and started over using the default setting in  Handbreak.  (Mpeg4)  Things went much better and using DeVeDe I was able  to start burning a VCD.  But at some point it gives me an error.   "Probably a buffer underrun occurred.  Please use a lower burn speed."   So I cut the burn speed in half but get the same error message.  I have  copied the debugging output from the first time below and followed it  with the debugging output from the last time.  Any suggestion would be  appreciated.  

 [FONT=monospace]Devices[/FONT]
 [FONT=monospace]-----------------------[/FONT]
 [FONT=monospace]TSSTcorp CDDVDW SH-224BB SB00 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump] [%7][/FONT]
 [FONT=monospace]
[/FONT]
 [FONT=monospace]System[/FONT]
 [FONT=monospace]-----------------------[/FONT]
 [FONT=monospace]K3b Version: 17.12.3[/FONT]
 [FONT=monospace]KDE Version: 5.44.0[/FONT]
 [FONT=monospace]Qt Version:  5.9.5[/FONT]
 [FONT=monospace]Kernel:      4.15.0-46-generic[/FONT]
 [FONT=monospace]
[/FONT]
 [FONT=monospace]Used versions[/FONT]
 [FONT=monospace]-----------------------[/FONT]
 [FONT=monospace]cdrecord: 1.1.11[/FONT]
 [FONT=monospace]
[/FONT]
 [FONT=monospace]cdrecord[/FONT]
 [FONT=monospace]-----------------------[/FONT]
 [FONT=monospace]scsidev: '/dev/sr0'[/FONT]
 [FONT=monospace]devname: '/dev/sr0'[/FONT]
 [FONT=monospace]scsibus: -2 target: -2 lun: -2[/FONT]
 [FONT=monospace]Linux sg driver version: 3.5.27[/FONT]
 [FONT=monospace]Wodim version: 1.1.11[/FONT]
 [FONT=monospace]SCSI buffer size: 64512[/FONT]
 [FONT=monospace]Beginning DMA speed test. Set CDR_NODMATEST environment variable if device[/FONT]
 [FONT=monospace]communication breaks or freezes immediately after that.[/FONT]
 [FONT=monospace]TOC Type: 1 = CD-ROM[/FONT]
 [FONT=monospace]Driveropts: 'burnfree'[/FONT]
 [FONT=monospace]Device type    : Removable CD-ROM[/FONT]
 [FONT=monospace]Version        : 5[/FONT]
 [FONT=monospace]Response Format: 2[/FONT]
 [FONT=monospace]Capabilities   : [/FONT]
 [FONT=monospace]Vendor_info    : 'TSSTcorp'[/FONT]
 [FONT=monospace]Identification : 'CDDVDW SH-224BB '[/FONT]
 [FONT=monospace]Revision       : 'SB00'[/FONT]
 [FONT=monospace]Device seems to be: Generic mmc2 DVD-R/DVD-RW.[/FONT]
 [FONT=monospace]Current: 0x0009 (CD-R)[/FONT]
 [FONT=monospace]Profile: 0x0015 (DVD-R/DL sequential recording) [/FONT]
 [FONT=monospace]Profile: 0x0016 (DVD-R/DL layer jump recording) [/FONT]
 [FONT=monospace]Profile: 0x002B (DVD+R/DL) [/FONT]
 [FONT=monospace]Profile: 0x001B (DVD+R) [/FONT]
 [FONT=monospace]Profile: 0x001A (DVD+RW) [/FONT]
 [FONT=monospace]Profile: 0x0014 (DVD-RW sequential recording) [/FONT]
 [FONT=monospace]Profile: 0x0013 (DVD-RW restricted overwrite) [/FONT]
 [FONT=monospace]Profile: 0x0012 (DVD-RAM) [/FONT]
 [FONT=monospace]Profile: 0x0011 (DVD-R sequential recording) [/FONT]
 [FONT=monospace]Profile: 0x0010 (DVD-ROM) [/FONT]
 [FONT=monospace]Profile: 0x000A (CD-RW) [/FONT]
 [FONT=monospace]Profile: 0x0009 (CD-R) (current)[/FONT]
 [FONT=monospace]Profile: 0x0008 (CD-ROM) [/FONT]
 [FONT=monospace]Profile: 0x0002 (Removable disk) [/FONT]
 [FONT=monospace]Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).[/FONT]
 [FONT=monospace]Driver flags   : MMC-3 SWABAUDIO BURNFREE [/FONT]
 [FONT=monospace]Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R[/FONT]
 [FONT=monospace]Drive buf size : 1286912 = 1256 KB[/FONT]
 [FONT=monospace]FIFO size      : 12582912 = 12288 KB[/FONT]
 [FONT=monospace]Speed set to 8468 KB/s[/FONT]
 [FONT=monospace]Track 01: data     1 MB        [/FONT]
 [FONT=monospace]Track 02: data    59 MB        [/FONT]
 [FONT=monospace]Track 03: data    52 MB        [/FONT]
 [FONT=monospace]Track 04: data    56 MB        [/FONT]
 [FONT=monospace]Track 05: data    67 MB        [/FONT]
 [FONT=monospace]Track 06: data    64 MB        [/FONT]
 [FONT=monospace]Track 07: data    62 MB        [/FONT]
 [FONT=monospace]Track 08: data    61 MB        [/FONT]
 [FONT=monospace]Track 09: data    56 MB        [/FONT]
 [FONT=monospace]Track 10: data    70 MB        [/FONT]
 [FONT=monospace]Track 11: data    60 MB        [/FONT]
 [FONT=monospace]Total size:      613 MB (60:45.13) = 273385 sectors[/FONT]
 [FONT=monospace]Lout start:      613 MB (60:47/10) = 273385 sectors[/FONT]
 [FONT=monospace]Current Secsize: 2048[/FONT]
 [FONT=monospace]ATIP info from disk:[/FONT]
 [FONT=monospace]  Indicated writing power: 7[/FONT]
 [FONT=monospace]  Is not unrestricted[/FONT]
 [FONT=monospace]  Is not erasable[/FONT]
 [FONT=monospace]  ATIP start of lead in:  -11597 (97:27/28)[/FONT]
 [FONT=monospace]  ATIP start of lead out: 359849 (79:59/74)[/FONT]
 [FONT=monospace]Disk type:    Short strategy type (Phthalocyanine or similar)[/FONT]
 [FONT=monospace]Manuf. index: 20[/FONT]
 [FONT=monospace]Manufacturer: Princo Corporation[/FONT]
 [FONT=monospace]Blocks total: 359849 Blocks current: 359849 Blocks remaining: 86464[/FONT]
 [FONT=monospace]Starting to write CD/DVD at speed  48.0 in real SAO mode for single session.[/FONT]
 [FONT=monospace]Last chance to quit, starting real write in    2 seconds.[/FONT]
 [FONT=monospace]   1 seconds.[/FONT]
 [FONT=monospace]   0 seconds. Operation starts.[/FONT]
 [FONT=monospace]Waiting for reader process to fill input buffer ... input buffer ready.[/FONT]
 [FONT=monospace]Performing OPC...[/FONT]
 [FONT=monospace]Sending CUE sheet...[/FONT]
 [FONT=monospace]Writing pregap for track 1 at -150[/FONT]
 [FONT=monospace]Starting new track at sector: 0[/FONT]
 [FONT=monospace]Track 01:    0 of    1 MB written.[/FONT]
 [FONT=monospace]Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error[/FONT]
 [FONT=monospace]CDB:  2A 00 00 00 00 51 00 00 1B 00[/FONT]
 [FONT=monospace]status: 0x2 (CHECK CONDITION)[/FONT]
 [FONT=monospace]Sense Bytes: 71 00 03 00 00 00 00 0A 00 00 00 00 0C 00 00 00[/FONT]
 [FONT=monospace]Sense Key: 0x3 Medium Error, deferred error, Segment 0[/FONT]
 [FONT=monospace]Sense Code: 0x0C Qual 0x00 (write error) Fru 0x0[/FONT]
 [FONT=monospace]Sense flags: Blk 0 (not valid) [/FONT]
 [FONT=monospace]cmd finished after 0.027s timeout 200s[/FONT]
 [FONT=monospace]/usr/bin/wodim: A write error occured.[/FONT]
 [FONT=monospace]/usr/bin/wodim: Please properly read the error message above.[/FONT]
 [FONT=monospace]write track data: error after 190512 bytes[/FONT]
 [FONT=monospace]Writing  time:  306.314s[/FONT]
 [FONT=monospace]Average write speed  19.5x.[/FONT]
 [FONT=monospace]Fixating...[/FONT]
 [FONT=monospace]Fixating time:    0.003s[/FONT]
 [FONT=monospace]/usr/bin/wodim: fifo had 194 puts and 4 gets.[/FONT]
 [FONT=monospace]/usr/bin/wodim: fifo was 0 times empty and 2 times full, min fill was 98%.[/FONT]
 [FONT=monospace]BURN-Free was never needed.[/FONT]
 [FONT=monospace]
[/FONT]
 [FONT=monospace]cdrecord command:[/FONT]
 [FONT=monospace]-----------------------[/FONT]
 [FONT=monospace]/usr/bin/wodim -v gracetime=2 dev=/dev/sr0 speed=48 -sao driveropts=burnfree cuefile=/home/mlempenau/Copy/movie/movie.cue[/FONT]
 [FONT=monospace]
 [/FONT]
[FONT=monospace]Devices[/FONT]
 [FONT=monospace]-----------------------[/FONT]
 [FONT=monospace]TSSTcorp CDDVDW SH-224BB SB00 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump] [%7][/FONT]
 [FONT=monospace]
[/FONT]
 [FONT=monospace]System[/FONT]
 [FONT=monospace]-----------------------[/FONT]
 [FONT=monospace]K3b Version: 17.12.3[/FONT]
 [FONT=monospace]KDE Version: 5.44.0[/FONT]
 [FONT=monospace]Qt Version:  5.9.5[/FONT]
 [FONT=monospace]Kernel:      4.15.0-46-generic[/FONT]
 [FONT=monospace]
[/FONT]
 [FONT=monospace]Used versions[/FONT]
 [FONT=monospace]-----------------------[/FONT]
 [FONT=monospace]cdrecord: 1.1.11[/FONT]
 [FONT=monospace]
[/FONT]
 [FONT=monospace]cdrecord[/FONT]
 [FONT=monospace]-----------------------[/FONT]
 [FONT=monospace]scsidev: '/dev/sr0'[/FONT]
 [FONT=monospace]devname: '/dev/sr0'[/FONT]
 [FONT=monospace]scsibus: -2 target: -2 lun: -2[/FONT]
 [FONT=monospace]Linux sg driver version: 3.5.27[/FONT]
 [FONT=monospace]Wodim version: 1.1.11[/FONT]
 [FONT=monospace]SCSI buffer size: 64512[/FONT]
 [FONT=monospace]Beginning DMA speed test. Set CDR_NODMATEST environment variable if device[/FONT]
 [FONT=monospace]communication breaks or freezes immediately after that.[/FONT]
 [FONT=monospace]TOC Type: 1 = CD-ROM[/FONT]
 [FONT=monospace]Driveropts: 'burnfree'[/FONT]
 [FONT=monospace]Device type    : Removable CD-ROM[/FONT]
 [FONT=monospace]Version        : 5[/FONT]
 [FONT=monospace]Response Format: 2[/FONT]
 [FONT=monospace]Capabilities   : [/FONT]
 [FONT=monospace]Vendor_info    : 'TSSTcorp'[/FONT]
 [FONT=monospace]Identification : 'CDDVDW SH-224BB '[/FONT]
 [FONT=monospace]Revision       : 'SB00'[/FONT]
 [FONT=monospace]Device seems to be: Generic mmc2 DVD-R/DVD-RW.[/FONT]
 [FONT=monospace]Current: 0x0009 (CD-R)[/FONT]
 [FONT=monospace]Profile: 0x0015 (DVD-R/DL sequential recording) [/FONT]
 [FONT=monospace]Profile: 0x0016 (DVD-R/DL layer jump recording) [/FONT]
 [FONT=monospace]Profile: 0x002B (DVD+R/DL) [/FONT]
 [FONT=monospace]Profile: 0x001B (DVD+R) [/FONT]
 [FONT=monospace]Profile: 0x001A (DVD+RW) [/FONT]
 [FONT=monospace]Profile: 0x0014 (DVD-RW sequential recording) [/FONT]
 [FONT=monospace]Profile: 0x0013 (DVD-RW restricted overwrite) [/FONT]
 [FONT=monospace]Profile: 0x0012 (DVD-RAM) [/FONT]
 [FONT=monospace]Profile: 0x0011 (DVD-R sequential recording) [/FONT]
 [FONT=monospace]Profile: 0x0010 (DVD-ROM) [/FONT]
 [FONT=monospace]Profile: 0x000A (CD-RW) [/FONT]
 [FONT=monospace]Profile: 0x0009 (CD-R) (current)[/FONT]
 [FONT=monospace]Profile: 0x0008 (CD-ROM) [/FONT]
 [FONT=monospace]Profile: 0x0002 (Removable disk) [/FONT]
 [FONT=monospace]Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).[/FONT]
 [FONT=monospace]Driver flags   : MMC-3 SWABAUDIO BURNFREE [/FONT]
 [FONT=monospace]Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R[/FONT]
 [FONT=monospace]Drive buf size : 1286912 = 1256 KB[/FONT]
 [FONT=monospace]FIFO size      : 12582912 = 12288 KB[/FONT]
 [FONT=monospace]Speed set to 5645 KB/s[/FONT]
 [FONT=monospace]Track 01: data     1 MB        [/FONT]
 [FONT=monospace]Track 02: data    59 MB        [/FONT]
 [FONT=monospace]Track 03: data    52 MB        [/FONT]
 [FONT=monospace]Track 04: data    56 MB        [/FONT]
 [FONT=monospace]Track 05: data    67 MB        [/FONT]
 [FONT=monospace]Track 06: data    64 MB        [/FONT]
 [FONT=monospace]Track 07: data    62 MB        [/FONT]
 [FONT=monospace]Track 08: data    61 MB        [/FONT]
 [FONT=monospace]Track 09: data    56 MB        [/FONT]
 [FONT=monospace]Track 10: data    70 MB        [/FONT]
 [FONT=monospace]Track 11: data    60 MB        [/FONT]
 [FONT=monospace]Total size:      613 MB (60:45.13) = 273385 sectors[/FONT]
 [FONT=monospace]Lout start:      613 MB (60:47/10) = 273385 sectors[/FONT]
 [FONT=monospace]Current Secsize: 2048[/FONT]
 [FONT=monospace]ATIP info from disk:[/FONT]
 [FONT=monospace]  Indicated writing power: 7[/FONT]
 [FONT=monospace]  Is not unrestricted[/FONT]
 [FONT=monospace]  Is not erasable[/FONT]
 [FONT=monospace]  ATIP start of lead in:  -11597 (97:27/28)[/FONT]
 [FONT=monospace]  ATIP start of lead out: 359849 (79:59/74)[/FONT]
 [FONT=monospace]Disk type:    Short strategy type (Phthalocyanine or similar)[/FONT]
 [FONT=monospace]Manuf. index: 20[/FONT]
 [FONT=monospace]Manufacturer: Princo Corporation[/FONT]
 [FONT=monospace]Blocks total: 359849 Blocks current: 359849 Blocks remaining: 86464[/FONT]
 [FONT=monospace]Starting to write CD/DVD at speed  32.0 in real SAO mode for single session.[/FONT]
 [FONT=monospace]Last chance to quit, starting real write in    2 seconds.[/FONT]
 [FONT=monospace]   1 seconds.[/FONT]
 [FONT=monospace]   0 seconds. Operation starts.[/FONT]
 [FONT=monospace]Waiting for reader process to fill input buffer ... input buffer ready.[/FONT]
 [FONT=monospace]Performing OPC...[/FONT]
 [FONT=monospace]Sending CUE sheet...[/FONT]
 [FONT=monospace]Writing pregap for track 1 at -150[/FONT]
 [FONT=monospace]Starting new track at sector: 0[/FONT]
 [FONT=monospace]Track 01:    0 of    1 MB written.[/FONT]
 [FONT=monospace]Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error[/FONT]
 [FONT=monospace]CDB:  2A 00 00 00 00 51 00 00 1B 00[/FONT]
 [FONT=monospace]status: 0x2 (CHECK CONDITION)[/FONT]
 [FONT=monospace]Sense Bytes: 71 00 03 00 00 00 00 0A 00 00 00 00 0C 00 00 00[/FONT]
 [FONT=monospace]Sense Key: 0x3 Medium Error, deferred error, Segment 0[/FONT]
 [FONT=monospace]Sense Code: 0x0C Qual 0x00 (write error) Fru 0x0[/FONT]
 [FONT=monospace]Sense flags: Blk 0 (not valid) [/FONT]
 [FONT=monospace]cmd finished after 0.027s timeout 200s[/FONT]
 [FONT=monospace]/usr/bin/wodim: A write error occured.[/FONT]
 [FONT=monospace]/usr/bin/wodim: Please properly read the error message above.[/FONT]
 [FONT=monospace]write track data: error after 190512 bytes[/FONT]
 [FONT=monospace]Writing  time:  191.046s[/FONT]
 [FONT=monospace]Average write speed  22.5x.[/FONT]
 [FONT=monospace]Fixating...[/FONT]
 [FONT=monospace]Fixating time:    0.003s[/FONT]
 [FONT=monospace]/usr/bin/wodim: fifo had 194 puts and 4 gets.[/FONT]
 [FONT=monospace]/usr/bin/wodim: fifo was 0 times empty and 1 times full, min fill was 98%.[/FONT]
 [FONT=monospace]BURN-Free was never needed.[/FONT]
 [FONT=monospace]
[/FONT]
 [FONT=monospace]cdrecord command:[/FONT]
 [FONT=monospace]-----------------------[/FONT]
 [FONT=monospace]/usr/bin/wodim -v gracetime=2 dev=/dev/sr0 speed=32 -sao driveropts=burnfree cuefile=/home/mlempenau/Copy/movie/movie.cue[/FONT]

---

