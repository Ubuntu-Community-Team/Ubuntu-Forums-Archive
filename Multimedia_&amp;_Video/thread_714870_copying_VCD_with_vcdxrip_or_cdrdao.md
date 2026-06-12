---
title: "copying VCD with vcdxrip or cdrdao"
date: 2008-03-04
forum: Multimedia &amp; Video
---

### Post by nlz on 2008-03-04
i tried ripping a VCD with vcdxrip but i get an error everytime. 

```
qnuf@mediaction:~$ vcdxrip -p -v -C
++ WARN: detected wrong size calculation for form2 file `CDI/CDI_IMAG.RTF'; fixing up
!ASSERT: file mpeg.c: line 515 (_analyze_pes_header): assertion failed: (vcd_bitvec_peek_bits (buf, pos2, 8) == 0xff)
Aborted (core dumped)
```

dmesg mentions a I/0 error 

```
[10636.801906] end_request: I/O error, dev sr0, sector 1028
[10636.801914] Buffer I/O error on device sr0, logical block 257
[10636.805722] end_request: I/O error, dev sr0, sector 1024
[10636.805729] Buffer I/O error on device sr0, logical block 256
[10636.805734] Buffer I/O error on device sr0, logical block 257
[10636.837042] end_request: I/O error, dev sr0, sector 1024
[10636.837051] Buffer I/O error on device sr0, logical block 256
[10636.842483] end_request: I/O error, dev sr0, sector 1028
[10636.842491] Buffer I/O error on device sr0, logical block 257
[10636.998348] end_request: I/O error, dev sr0, sector 1024
[10636.998357] Buffer I/O error on device sr0, logical block 256
[10636.998364] Buffer I/O error on device sr0, logical block 257
[10637.019387] end_request: I/O error, dev sr0, sector 1024
[10637.153361] end_request: I/O error, dev sr0, sector 5032
[10637.157213] end_request: I/O error, dev sr0, sector 5036
[10637.161413] end_request: I/O error, dev sr0, sector 5032
[10637.165061] end_request: I/O error, dev sr0, sector 5036
[10637.168853] end_request: I/O error, dev sr0, sector 5040
[10637.172581] end_request: I/O error, dev sr0, sector 5044
[10637.176209] end_request: I/O error, dev sr0, sector 5040
```

then i tried to do it with cdrdao

```
qnuf@mediaction:~$ cdrdao copy /home/qnuf
Cdrdao version 1.2.2 - (C) Andreas Mueller <andreas@daneb.de>
  SCSI interface library - (C) Joerg Schilling
  Paranoia DAE library - (C) Monty

Check http://cdrdao.sourceforge.net/drives.html#dt for current driver tables.

Error trying to open /dev/cdrw exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/cdrw exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/cdrw exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/cdrw exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/cdrw exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/cdrw exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/cdrw exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/cdrw exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/cdrw exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/cdrw exclusively (Device or resource busy)... retrying in 1 second.
ERROR: Cannot open SCSI device '/dev/cdrw': Cannot open '/dev/cdrw'
Supported SCSI transports for this platform:

Transport name:         sg
Transport descr.:       Generic transport independent SCSI
Transp. layer ind.:
Target specifier:       bus,target,lun
Target example:         1,2,0
SCSI Bus scanning:      supported
Open via UNIX device:   not supported

Transport name:         pg
Transport descr.:       SCSI transport for ATAPI over Parallel Port
Transp. layer ind.:
Target specifier:       bus,target,lun
Target example:         1,2,0
SCSI Bus scanning:      supported
Open via UNIX device:   not supported

Transport name:         ATA
Transport descr.:       ATA Packet specific SCSI transport
Transp. layer ind.:     ATAPI:
Target specifier:       bus,target,lun
Target example:         ATAPI:1,2,0
SCSI Bus scanning:      supported
Open via UNIX device:   not supported

Transport name:         ATA
Transport descr.:       ATA Packet specific SCSI transport using sg interface
Transp. layer ind.:     ATA:
Target specifier:       bus,target,lun
Target example:         1,2,0
SCSI Bus scanning:      supported
Open via UNIX device:   not supported
ERROR: Please use option '--device [proto:]bus,id,lun', e.g. --device 0,6,0 or --device ATA:0,0,0
ERROR: Cannot setup device /dev/cdrw.


```

but it also doesn't work. When i acces /dev/cdrw it's just working as a working symbolic link to scd0.

So, how can i copy this cd to my harddrive? Only the *.dat file is also enough, don't care if i have to encode it or not..

---

