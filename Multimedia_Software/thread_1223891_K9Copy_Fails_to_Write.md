---
title: "K9Copy Fails to Write"
date: 2009-07-26
forum: Multimedia Software
---

### Post by risc427 on 2009-07-26
When trying to backup a DVD with K9Copy the following error is produced once it gets to the stage where it is actually writing the data to a DVD.

> 
I: -input-charset not specified, using utf-8 (detected in locale settings)

wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
Speed set to 5645 KB/s

  0.02% done, estimate finish Sun Jul 26 21:03:47 2009
  0.04% done, estimate finish Sun Jul 26 19:51:34 2009
  0.07% done, estimate finish Sun Jul 26 19:27:02 2009
  0.09% done, estimate finish Sun Jul 26 19:14:23 2009
  0.11% done, estimate finish Sun Jul 26 19:07:04 2009
  0.13% done, estimate finish Sun Jul 26 19:02:09 2009
  0.16% done, estimate finish Sun Jul 26 18:58:38 2009
  0.18% done, estimate finish Sun Jul 26 18:55:54 2009
  0.20% done, estimate finish Sun Jul 26 18:53:51 2009
  0.22% done, estimate finish Sun Jul 26 18:52:13 2009
  0.25% done, estimate finish Sun Jul 26 18:50:52 2009

Errno: 5 (Input/output error), reserve track scsi sendcmd: no error
CDB:  53 00 00 00 00 00 22 33 99 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 30 05 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x05 (cannot write medium - incompatible format) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.000s timeout 200s
wodim: Cannot open new session.



I've tried running K9 as root only to get the same error. I've also tried removing the memlock limits all together, but that doesn't seem to 
help either. 

I'm running 32-bit 9.04

Any help is much appreciated. :confused:

---

### Post by risc427 on 2009-07-27
Anyone? 

This issue seems to only occur when using 16x media. Very odd to me.

---

### Post by javajesse on 2009-12-03
Has anyone resolved this?  
 
It appears to be related to burning speed.  I have a Thinkpad W500 with the DVD+/-RW drive.
 
(1) how to control K9Copy burn rate ?
 
(2) what blank DVD speed should I use ?
 
Thanks, y'all

---

