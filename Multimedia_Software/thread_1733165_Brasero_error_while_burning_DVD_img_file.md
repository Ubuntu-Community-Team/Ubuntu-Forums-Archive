---
title: "Brasero error while burning DVD img file"
date: 2011-04-18
forum: Multimedia Software
---

### Post by roemhildtg on 2011-04-18
I was trying to burn a dvd to an image file today, and the first one worked no problem, I tried to burn another and I keep getting this error:
Data could not be written (Input/output error) 

Here's my log:

Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1744)
BraseroDvdcss called brasero_job_get_action
BraseroDvdcss called brasero_job_get_action
BraseroDvdcss called brasero_job_get_current_track
BraseroDvdcss called brasero_job_set_output_size_for_current_track
BraseroDvdcss stopping
BraseroDvdcss called brasero_job_get_action
BraseroDvdcss called brasero_job_get_session_output_size
BraseroDvdcss output set (IMAGE) image = /home/gregg/brasero-1.iso toc = none
BraseroDvdcss called brasero_job_get_session_output_size
BraseroDvdcss called brasero_job_get_action
BraseroDvdcss called brasero_job_set_use_average_rate
BraseroDvdcss called brasero_job_set_current_action
BraseroDvdcss called brasero_job_get_current_track
BraseroDvdcss DVD map created (keys retrieved)
BraseroDvdcss called brasero_job_set_current_action
BraseroDvdcss called brasero_job_get_fd_out
BraseroDvdcss called brasero_job_get_image_output
BraseroDvdcss called brasero_job_error
BraseroDvdcss finished with an error
BraseroDvdcss asked to stop because of an error
    error        = 1
    message    = "Data could not be written (Input/output error)"
BraseroDvdcss stopping
Session error : Data could not be written (Input/output error) (brasero_burn_record brasero-burn.c:2862)

Thanks guys.

---

### Post by marl30 on 2011-04-18
Brasero isn't the most reliable burning software. Do yourself a favor and install Gnome Baker or K3b, you'll have less issues burning stuff.

---

### Post by roemhildtg on 2011-04-19
Okay thanks for the advice, I just tried Gnome Baker, and the same sort of problem occurred. Instead of an error though, it gave the "Burn completed" message. Here is the output:

Read  speed:  5540 kB/s (CD  31x, DVD  4x).
Write speed:     0 kB/s (CD   0x, DVD  0x).
Capacity: 4096043 Blocks = 8192086 kBytes = 8000 MBytes = 8388 prMB
Sectorsize: 2048 Bytes
Copy from SCSI (4,0,0) disk to file '/home/gregg/gnomebaker.iso'
end:   4096043
addr:        0 cnt: 64 Errno: 5 (Input/output error), read_g1 scsi sendcmd: no error
CDB:  28 00 00 02 24 80 00 00 40 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 6F 03 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x6F Qual 0x03 (read of scrambled sector without authentication) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.035s timeout 40s
readom: Input/output error. Cannot read source disk
readom: Retrying from sector 140416.
................~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~+~~~-~~~
readom: Input/output error. Error on sector 140431 not corrected. Total of 1 errors.

Time total: 157.402sec
Read 280832.00 kB at 1784.2 kB/sec.
Max corected retry count was 0 (limited to 128).
The following 1 sector(s) could not be read correctly:
140431

Looks like I'll try k3b..

---

### Post by marl30 on 2011-04-20
Try k3b as well. If you you're still getting the same error, perhaps it's the drive.

---

### Post by MepisReign on 2011-04-20
Is the DVD that you are trying to burn copy-protected?
If that is the case you need libdvdcss, it can be found in medibuntu (google for it)

Best Regards,

MepisReign

---

### Post by roemhildtg on 2011-04-21
The dvd is copy protected, I am trying to burn it to my computer so I can eventually convert it for my mp3/mp4 player. 

I am fairly certain the issue is not with the drive, I successfully burned a different dvd to a file, it may be just a problem with the formatting in this disk? 

k3b supposedly accomplished the burning process, however the img file, which should have been around 8gb was only about 200mb, and the img file was not readable..

I finally decided just to convert the file right off the disk with handbrake, and this seems to be a temporary solution..thanks for your help though anyways guys.

---

