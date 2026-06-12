---
title: "Brasero fails to burn audio CD catastrophically"
date: 2010-04-28
forum: Multimedia Software
---

### Post by Tsela on 2010-04-28
Hi everyone!

I am new to the Ubuntu Forums, so forgive me if I get this wrong.

I bought a new computer 2 months ago, pre-installed with Ubuntu Karmic Koala (from a small local company that specialises in Ubuntu computers). The thing works like a charm, and I'm getting used to Ubuntu (I used to run Debian as a desktop on my old computer). I have one annoying problem though: Brasero fails every time I try to burn an Audio CD from a bunch of mp3s.

Converting the mp3s themselves works without a problem, but as soon as the burning itself starts, it slows down to a crawl (while the DVD-rewriter spins at full speed), and eventually Brasero tells me the burning failed. Brasero itself does not crash, and returns to its normal window, however it leaves my DVD-rewriter in an unusable state: the CD in there keeps spinning, and the DVD-rewriter doesn't react to pushing the eject button. Not only that, but on the software side Ubuntu reports the DVD-rewriter as being empty and idle, and I can't stop it nor eject the CD from there! The only way I can get it to stop spinning and eventually remove the CD (which is now unusable, I checked) is by shutting down the computer completely.

I've tried slowing down the burning speed, without effect. I've tried saving the image first to disc before burning, without effect either. The problem only happens with audio CDs: I can burn data CDs and DVDs without a single issue. I'm not a Linux newbie, but I must admit this problem is giving me headaches.

So before I file in a bug report in Launchpad, I wonder whether the community could help me here. Has anyone had the same problem, or a similar one? If so, how have you solved it? Am I doing something wrong? I can't believe it is the hardware that is at fault, as burning data CDs works great, and the computer has been built specially with components that are 100% Linux-compatible (that's one of the guarantees of the company I bought it from).

Here's an excerpt of the error log I get back from Brasero when the burning fails (I've removed the transcoding part, keeping only the part about Wodim):

```
Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1848)

[snipped BraseroTranscode logging info. All transcodes were successful]

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
BraseroWodim called brasero_job_get_audio_title
BraseroWodim called brasero_job_get_tracks
BraseroWodim called brasero_job_get_fd_in
BraseroWodim writing inf (/tmp/brasero_tmp_I4DUBV.inf)
BraseroWodim got track length 154540402368 11591
BraseroWodim called brasero_job_get_fd_in
BraseroWodim writing inf (/tmp/brasero_tmp_A5GOBV.inf)
BraseroWodim got track length 202396727104 15180
BraseroWodim called brasero_job_get_fd_in
BraseroWodim writing inf (/tmp/brasero_tmp_4AHPBV.inf)
BraseroWodim got track length 117577138448 8819
BraseroWodim called brasero_job_get_fd_in
BraseroWodim writing inf (/tmp/brasero_tmp_8AALBV.inf)
BraseroWodim got track length 207046522848 15529
BraseroWodim called brasero_job_get_fd_in
BraseroWodim writing inf (/tmp/brasero_tmp_A4U0BV.inf)
BraseroWodim got track length 167941218192 12596
BraseroWodim called brasero_job_get_fd_in
BraseroWodim writing inf (/tmp/brasero_tmp_YWFRBV.inf)
BraseroWodim got track length 224626930352 16848
BraseroWodim called brasero_job_get_fd_in
BraseroWodim writing inf (/tmp/brasero_tmp_TTWUBV.inf)
BraseroWodim got track length 207960808528 15598
BraseroWodim called brasero_job_get_fd_in
BraseroWodim writing inf (/tmp/brasero_tmp_E03TBV.inf)
BraseroWodim got track length 246204072400 18466
BraseroWodim called brasero_job_get_fd_in
BraseroWodim writing inf (/tmp/brasero_tmp_RHAKBV.inf)
BraseroWodim got track length 220839175392 16563
BraseroWodim called brasero_job_get_fd_in
BraseroWodim writing inf (/tmp/brasero_tmp_1DJ2BV.inf)
BraseroWodim got track length 239020399200 17927
BraseroWodim called brasero_job_get_fd_in
BraseroWodim writing inf (/tmp/brasero_tmp_ZT4TBV.inf)
BraseroWodim got track length 183614686992 13772
BraseroWodim called brasero_job_get_fd_in
BraseroWodim writing inf (/tmp/brasero_tmp_5132BV.inf)
BraseroWodim got track length 188865299040 14165
BraseroWodim called brasero_job_get_fd_in
BraseroWodim writing inf (/tmp/brasero_tmp_0WI2BV.inf)
BraseroWodim got track length 202475094448 15186
BraseroWodim called brasero_job_get_fd_in
BraseroWodim writing inf (/tmp/brasero_tmp_17WNBV.inf)
BraseroWodim got track length 267075908352 20031
BraseroWodim called brasero_job_get_tracks
BraseroWodim called brasero_job_set_current_action
BraseroWodim got varg:
        wodim
        -v
        dev=/dev/sr0
        speed=48
        driveropts=burnfree
        -dao
        fs=16m
        -audio
        -swab
        -pad
        -useinfo
        -text
        /tmp/brasero_tmp_I4DUBV.cdr
        /tmp/brasero_tmp_A5GOBV.cdr
        /tmp/brasero_tmp_4AHPBV.cdr
        /tmp/brasero_tmp_8AALBV.cdr
        /tmp/brasero_tmp_A4U0BV.cdr
        /tmp/brasero_tmp_YWFRBV.cdr
        /tmp/brasero_tmp_TTWUBV.cdr
        /tmp/brasero_tmp_E03TBV.cdr
        /tmp/brasero_tmp_RHAKBV.cdr
        /tmp/brasero_tmp_1DJ2BV.cdr
        /tmp/brasero_tmp_ZT4TBV.cdr
        /tmp/brasero_tmp_5132BV.cdr
        /tmp/brasero_tmp_0WI2BV.cdr
        /tmp/brasero_tmp_17WNBV.cdr
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
BraseroWodim stdout: TOC Type: 0 = CD-DA
BraseroWodim stdout: Driveropts: 'burnfree'
BraseroWodim stdout: Device type    : Removable CD-ROM
BraseroWodim stdout: Version        : 5
BraseroWodim stdout: Response Format: 2
BraseroWodim stdout: Capabilities   : 
BraseroWodim stdout: Vendor_info    : 'TSSTcorp'
BraseroWodim stdout: Identification : 'CDDVDW SH-S223C '
BraseroWodim stdout: Revision       : 'SB01'
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
BraseroWodim stdout: Profile: 0x0008 (CD-ROM) 
BraseroWodim stdout: Profile: 0x0002 (Removable disk) 
BraseroWodim stdout: Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
BraseroWodim stdout: Driver flags   : MMC-3 SWABAUDIO BURNFREE 
BraseroWodim stdout: Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
BraseroWodim stdout: Drive buf size : 720896 = 704 KB
BraseroWodim stdout: FIFO size      : 16777216 = 16384 KB
BraseroWodim stderr: Speed set to 8467 KB/s
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: pregap1: -1
BraseroWodim stdout: Track 01: audio   25 MB (02:34.54) no preemp copy
BraseroWodim stdout: Track 02: audio   34 MB (03:22.40) no preemp copy
BraseroWodim stdout: Track 03: audio   19 MB (01:57.58) no preemp copy
BraseroWodim stdout: Track 04: audio   34 MB (03:27.05) no preemp copy
BraseroWodim stdout: Track 05: audio   28 MB (02:47.94) no preemp copy
BraseroWodim stdout: Track 06: audio   37 MB (03:44.64) no preemp copy
BraseroWodim stdout: Track 07: audio   34 MB (03:27.97) no preemp copy
BraseroWodim stdout: Track 08: audio   41 MB (04:06.21) no preemp copy
BraseroWodim stdout: Track 09: audio   37 MB (03:40.84) no preemp copy
BraseroWodim stdout: Track 10: audio   40 MB (03:59.02) no preemp copy
BraseroWodim stdout: Track 11: audio   30 MB (03:03.62) no preemp copy
BraseroWodim stdout: Track 12: audio   31 MB (03:08.86) no preemp copy
BraseroWodim stdout: Track 13: audio   34 MB (03:22.48) no preemp copy
BraseroWodim stdout: Track 14: audio   44 MB (04:27.08) no preemp copy
BraseroWodim stdout: Total size:      476 MB (47:10.28) = 212271 sectors
BraseroWodim stdout: Lout start:      476 MB (47:12/21) = 212271 sectors
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
BraseroWodim stdout: Blocks total: 359845 Blocks current: 359845 Blocks remaining: 147574
BraseroWodim stdout: Starting to write CD/DVD at speed  48.0 in real SAO mode for single session.
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
BraseroWodim stdout: Sending CUE sheet...
BraseroWodim called brasero_job_get_input_type
BraseroWodim called brasero_job_set_current_action
BraseroWodim stderr: Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: CDB:  2A 00 FF FF FE 40 00 01 2A 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: status: 0x2 (CHECK CONDITION)
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: SAO startsec: -12508
BraseroWodim stderr: Sense Bytes: 72 0B 00 00 00 00 00 0E 09 0C 00 34 00 03 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Writing lead-in...
BraseroWodim stderr: Sense Key: 0x0 No Additional Sense, Segment 11
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: write CD-Text data: error after 1157760 bytes
BraseroWodim stderr: Sense Code: 0x00 Qual 0x03 (setmark detected) Fru 0x0
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Writing  time:  169.549s
BraseroWodim stderr: Sense flags: Blk 0 (not valid) 
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: cmd finished after 149.304s timeout 200s
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Could not write Lead-in.
BraseroWodim called brasero_job_get_flags
BraseroWodim called brasero_job_error
BraseroWodim finished with an error
BraseroWodim asked to stop because of an error
        error           = 15
        message = "An error occurred while writing to disc"
BraseroWodim stopping
BraseroWodim got killed
Session error : An error occurred while writing to disc (brasero_burn_record brasero-burn.c:2808)
```I've tried to read it, but I can't make heads or tails of it.

My computer has an AMD X4 965 Phenom quadcore processor on an Asus motherboard, a 1TB hard drive and 4GB of RAM, and runs an up-to-date installation of Ubuntu Karmic koala 32bit (with all important, recommended and proposed updates, and all media codecs installed). The DVD-rewriter is rather run-of-the-mill (the log above gives vendor and model info).

I hope someone can help me at least diagnose the problem (so that I can send a good bug report), as I just don't understand what's going on. It's annoying and discouraging that such a problem persists when everything else works just fine.

Thanks in advance for your help.

Cheers,
Christophe.

**Update:** upgrading to Lucid fixed the issue! Now I can create audio CDs without a problem!

---

