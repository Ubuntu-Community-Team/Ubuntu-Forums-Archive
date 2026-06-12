---
title: "CD burner ISO won't burn"
date: 2007-09-08
forum: Multimedia &amp; Video
---

### Post by American_Outcast on 2007-09-08
I tried Gnomebaker and K3B. Then I tried the command line to see what was going on. For some reason I can't burn iso images at all. I know it is not the burner itself. Here is all the command line info I got including the error about it being unable to fixate the disk, etc. Anyone have ideas on how to handle this or can someone point me to a post (or url,)  if one exists that explains and solves this problem? Thanks.

Edit: By the way the ISO itself is fine and not corrupt.

sudo cdrecord /home/me/Desktop/mycd.iso
Password:
wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
Quickly guessing the name of a drive capable to write CD-R, please wait...
Found /dev/cdrw, assuming dev=/dev/cdrw
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'Memorex '
Identification : '52MAXX 2452AJ   '
Revision       : '6WS5'
Device seems to be: Generic mmc CD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE FORCESPEED 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Speed set to 9152 KB/s
Starting to write CD/DVD at speed  52.0 in real TAO mode for single session.
Last chance to quit, starting real write    0 seconds. Operation starts.
Track 01: Total bytes read/written: 731668480/731668480 (357260 sectors).
Errno: 0 (Success), flush cache scsi sendcmd: no error
CDB:  35 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 0A 00 00 00 00 0C 00 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x0C Qual 0x00 (write error) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 4.236s timeout 120s
Trouble flushing the cache
wodim: Cannot close track.
Errno: 0 (Success), close track/session scsi sendcmd: no error
CDB:  5B 00 02 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 0A 00 00 00 00 72 00 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x72 Qual 0x00 (session fixation error) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 11.363s timeout 480s
cmd finished after 11.363s timeout 480s
wodim: Cannot fixate disk.

---

### Post by steveneddy on 2007-09-08
Maybe a bad CD?

Or there is already a table on the CD.

Change to a new CD.

---

### Post by American_Outcast on 2007-09-09
I tried that. I went through about 6 cd's already.

---

### Post by American_Outcast on 2007-09-09
12 hour Bump

---

### Post by American_Outcast on 2007-09-09
I have been running some tests. I remember having this problem before and I thought it was the cdburner. I now know it is not. I am still not sure what the problem is but I am pretty sure it has to do with the motherboard. I think I have added and upgraded beyond what it can handle, well handle 100% problem free.

---

### Post by American_Outcast on 2007-09-13
I reinstalled Ubuntu two days ago for an unrelated issue. Just for the hell of it I tried to burn an ISO today. It burnt and fixated just fine. Weird. If I have this problem again I am going to boot up XP and try to burn an iso there. Its a Memorex 52x24x52, maybe it just doesn't get along with Linux in general.

---

