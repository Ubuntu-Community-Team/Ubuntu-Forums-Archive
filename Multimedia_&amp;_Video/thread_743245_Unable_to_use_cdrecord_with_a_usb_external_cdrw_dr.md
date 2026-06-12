---
title: "Unable to use cdrecord with a usb external cdrw drive"
date: 2008-04-02
forum: Multimedia &amp; Video
---

### Post by hazel on 2008-04-02
I am having trouble writing to a cdrw drive (AOpen EHW5224U) connected via a usb port. I can do it in nautilus but I don't like having to use nautilus, which is slow to load and mucks up my fluxbox desktop.

In Red Hat, using a 2.4 kernel, I used to use cdrecord for this kind of thing. Now with Ubuntu Dapper, using a 2.6.15 kernel, cdrecord doesn't work. It gives a warning of incompatibility with 2.6 kernels and then spews out the following errors:

Starting new track at sector: 0
Track 01:    3 of  584 MB written (fifo 100%) [buf  31%]  7.1x.cdrecord: \Input/output error. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 00 06 4C 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: F0 00 05 00 00 08 5A 0C 00 00 00 00 10 02 00 00
Sense Key: 0x5 Illegal Request, segment 0
Sense Code: 0x10 Qual 0x02 (id crc or ecc error) [No matching qualifier] Fru 0x0Sense flags: Blk 2138 (valid)
cmd finished after 0.065s timeout 40s

write track data: error after 3301376 bytes
cdrecord: a write error occurred.
cdrecord: Please properly read the error message above.

I tried using cdread instead but that expects a parallel port connection so it doesn't detect the drive.  Does anyone know how to cure this - or another way to write to this kind of drive?
************

Someone on another forum recommended wodim; there's no compiled version for Dapper but I downloaded and compiled the cdrkit source code. And it worked. Wodim will burn CDs on my drive.

---

