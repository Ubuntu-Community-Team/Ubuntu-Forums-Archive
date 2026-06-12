---
title: "I Can't burn Cd"
date: 2011-01-12
forum: Multimedia Software
---

### Post by Darth Trix on 2011-01-12
I have tried to burn CD with different applications (Brasero, K3B, Gnome Baker) and it never works.
There's an attachment of the error log from Brasero
Also this is the last part of the log frmo Gnome Baker:

Errno: 5 (Input/output error), flush cache scsi sendcmd: no error
CDB:  35 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 04 00 00 00 00 0E 00 00 00 00 09 00 00 00
Sense Key: 0x4 Hardware Error, Segment 0
Sense Code: 0x09 Qual 0x00 (track following error) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 40.407s timeout 120s
Fixating time:    0.006s
Errno: 5 (Input/output error), close track/session scsi sendcmd: no error
CDB:  5B 00 02 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0E 00 00 00 00 2C 04 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x2C Qual 0x04 (current program area is empty) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.002s timeout 480s
cmd finished after 0.002s timeout 480s
wodim: Cannot fixate disk.
wodim: fifo had 192 puts and 1 gets.
wodim: fifo was 0 times empty and 0 times full, min fill was 100%.

I would like to know if anybody has an idea of wot the problem is
Thanks

---

