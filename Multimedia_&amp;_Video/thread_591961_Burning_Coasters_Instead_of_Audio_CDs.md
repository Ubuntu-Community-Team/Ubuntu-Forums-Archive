---
title: "Burning Coasters Instead of Audio CDs"
date: 2007-10-25
forum: Multimedia &amp; Video
---

### Post by bpont on 2007-10-25
I keep trying to burn an audio cd with gnomebaker, but it keeps failing with the following error:

```
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Sending CUE sheet...
SAO startsec: -12369
Writing lead-in...
Lead-in write time:    2.551s
Writing pregap for track 1 at -150
Starting new track at sector: 0
cdrecord: Input/output error. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 03 2A DB 00 00 1B 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 12 00 00 00 00 0C 09 00 00
[B]Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x0C Qual 0x09 (write error - loss of streaming) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.013s timeout 200s
cdrecord: The current problem looks like a buffer underrun.
cdrecord: Try to use 'driveropts=burnfree'.
cdrecord: Make sure that you are root, enable DMA and check your HW/OS set up.

write track data: error after 34863696 bytes
Writing  time:  354.229s
Average write speed   8.0x.
Min drive buffer fill was 0%
Total of 17 possible drive buffer underruns predicted.[/B]
Fixating...
Fixating time:    0.004s
cdrecord: fifo had 7758 puts and 7695 gets.
cdrecord: fifo was 0 times empty and 3865 times full, min fill was 84%.
```

Also, if I try using serpentine, instead of gnomebaker, it keeps prompting me to insert a blank cd when there already is one present, but it doesn't 'see' it for some reason!

](*,)

---

