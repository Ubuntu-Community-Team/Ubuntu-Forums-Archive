---
title: "USB cd burning issues"
date: 2007-02-28
forum: Multimedia &amp; Video
---

### Post by jaymode on 2007-02-28
I am having issues trying to burn a cd and it is very frustrating. I am trying to use GnomeBaker and I get this error message:

```

cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
cdrecord: Warning: Running on Linux-2.6.17-11-generic
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '4,0,0'
scsibus: 4 target: 0 lun: 0
Linux sg driver version: 3.5.33
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c	1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
cdrecord: This version of cdrecord does not include DVD-R/DVD-RW support code.
cdrecord: See /usr/share/doc/cdrecord/README.DVD.Debian for details on DVD support.
Cdrecord-Clone 2.01.01a03 (i686-pc-linux-gnu) Copyright (C) 1995-2005 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

TOC Type: 3 = CD-ROM XA mode 2
Using libscg version 'debian-0.8debian2'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'BENQ    '
Identifikation : 'DVD DD DW1650   '
Revision       : 'BCIC'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009
Profile: 0x002B 
Profile: 0x001B 
Profile: 0x001A 
Profile: 0x0016 
Profile: 0x0015 
Profile: 0x0014 
Profile: 0x0013 
Profile: 0x0011 
Profile: 0x0010 
Profile: 0x000A 
Profile: 0x0009 (current)
Profile: 0x0008 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96R RAW/R16 RAW/R96R
Drive buf size : 1073152 = 1048 KB
FIFO size      : 4194304 = 4096 KB
   4 seconds.   3 seconds.   2 seconds.   1 seconds.   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is OFF.
Turning BURN-Free on
Performing OPC...
Starting new track at sector: 0
cdrecord: Cannot allocate memory. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 00 00 00 00 00 1F 00
status: 0x0 (GOOD STATUS)
cmd finished after 0.000s timeout 40s
cdrecord: A write error occured.
cdrecord: Please properly read the error message above.

write track data: error after 0 bytes
Writing  time:    5.857s
Average write speed 946.2x.
Fixating...
Fixating time:    0.005s
cdrecord: fifo had 64 puts and 1 gets.
cdrecord: fifo was 0 times empty and 0 times full, min fill was 100%.
```


Then this is from dmesg:

```
[17332742.816000] usb 5-4.3: new high speed USB device using ehci_hcd and address 6
[17332742.920000] usb 5-4.3: configuration #1 chosen from 1 choice
[17332742.920000] scsi4 : SCSI emulation for USB Mass Storage devices
[17332742.920000] usb-storage: device found at 6
[17332742.920000] usb-storage: waiting for device to settle before scanning
[17332747.920000] usb-storage: device scan complete
[17332747.924000]   Vendor: BENQ      Model: DVD DD DW1650     Rev: BCIC
[17332747.924000]   Type:   CD-ROM                             ANSI SCSI revision: 00
[17332747.924000]  4:0:0:0: Attached scsi generic sg0 type 5
[17332747.980000] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[17332747.980000] Uniform CD-ROM driver Revision: 3.20
[17332747.980000] sr 4:0:0:0: Attached scsi CD-ROM sr0
[17332770.432000] UDF-fs: No VRS found
[17332770.484000] UDF-fs: No VRS found
[17332770.592000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17332770.596000] ISOFS: changing to secondary root
[17332959.092000] end_request: I/O error, dev sr0, sector 3168
[17332959.092000] ISOFS: unable to read i-node block
[17332959.096000] end_request: I/O error, dev sr0, sector 3184
[17332959.096000] ISOFS: unable to read i-node block
[17332959.100000] end_request: I/O error, dev sr0, sector 3212
[17332959.100000] ISOFS: unable to read i-node block
[17332959.104000] end_request: I/O error, dev sr0, sector 3216
[17332959.104000] ISOFS: unable to read i-node block
[17332959.108000] end_request: I/O error, dev sr0, sector 3236
[17332959.108000] ISOFS: unable to read i-node block
[17332959.116000] end_request: I/O error, dev sr0, sector 3296
[17332959.116000] ISOFS: unable to read i-node block
[17332959.120000] end_request: I/O error, dev sr0, sector 3312
[17332959.120000] ISOFS: unable to read i-node block
[17332959.128000] end_request: I/O error, dev sr0, sector 3344
[17332959.128000] ISOFS: unable to read i-node block
[17332959.132000] end_request: I/O error, dev sr0, sector 3372
[17332959.132000] ISOFS: unable to read i-node block
[17332959.136000] end_request: I/O error, dev sr0, sector 3444
[17332959.136000] ISOFS: unable to read i-node block
[17332959.140000] end_request: I/O error, dev sr0, sector 3512
[17332959.140000] ISOFS: unable to read i-node block
[17332959.144000] end_request: I/O error, dev sr0, sector 3536
[17332959.144000] ISOFS: unable to read i-node block
[17332959.148000] end_request: I/O error, dev sr0, sector 3568
[17332959.148000] ISOFS: unable to read i-node block
[17332959.148000] end_request: I/O error, dev sr0, sector 3616
[17332959.148000] ISOFS: unable to read i-node block
[17332959.152000] end_request: I/O error, dev sr0, sector 4344
[17332959.168000] ISOFS: unable to read i-node block
[17332959.172000] end_request: I/O error, dev sr0, sector 4356
[17332959.172000] ISOFS: unable to read i-node block
[17332959.176000] end_request: I/O error, dev sr0, sector 4368
[17332959.176000] ISOFS: unable to read i-node block
[17332959.180000] end_request: I/O error, dev sr0, sector 4376
[17332959.180000] ISOFS: unable to read i-node block
[17332959.184000] end_request: I/O error, dev sr0, sector 4396
[17332959.184000] ISOFS: unable to read i-node block
[17332959.188000] end_request: I/O error, dev sr0, sector 4416
[17332959.188000] ISOFS: unable to read i-node block
[17332959.192000] end_request: I/O error, dev sr0, sector 4420
[17332959.192000] ISOFS: unable to read i-node block
[17332959.196000] end_request: I/O error, dev sr0, sector 4504
[17332959.196000] ISOFS: unable to read i-node block
[17332959.200000] end_request: I/O error, dev sr0, sector 4568
[17332959.200000] ISOFS: unable to read i-node block
[17332959.204000] end_request: I/O error, dev sr0, sector 4656
[17332959.204000] ISOFS: unable to read i-node block
[17332959.208000] end_request: I/O error, dev sr0, sector 4672
[17332959.208000] ISOFS: unable to read i-node block
[17332959.212000] end_request: I/O error, dev sr0, sector 4676
[17332959.212000] ISOFS: unable to read i-node block
[17332959.216000] end_request: I/O error, dev sr0, sector 4812
[17332959.216000] ISOFS: unable to read i-node block
[17332959.220000] end_request: I/O error, dev sr0, sector 4992
[17332959.220000] ISOFS: unable to read i-node block
[17332959.224000] end_request: I/O error, dev sr0, sector 5000
[17332959.228000] ISOFS: unable to read i-node block
[17332959.232000] end_request: I/O error, dev sr0, sector 5012
[17332959.232000] ISOFS: unable to read i-node block
[17332959.240000] end_request: I/O error, dev sr0, sector 5020
[17332959.240000] ISOFS: unable to read i-node block
[17332959.240000] end_request: I/O error, dev sr0, sector 5028
[17332959.240000] ISOFS: unable to read i-node block
[17332959.244000] end_request: I/O error, dev sr0, sector 5040
[17332959.244000] ISOFS: unable to read i-node block
[17332959.248000] end_request: I/O error, dev sr0, sector 5064
[17332959.248000] ISOFS: unable to read i-node block
[17332959.252000] end_request: I/O error, dev sr0, sector 5084
[17332959.252000] ISOFS: unable to read i-node block
[17332959.256000] end_request: I/O error, dev sr0, sector 5112
[17332959.256000] ISOFS: unable to read i-node block
[17332959.260000] end_request: I/O error, dev sr0, sector 5116
[17332959.260000] ISOFS: unable to read i-node block
[17332959.260000] end_request: I/O error, dev sr0, sector 5128
[17332959.260000] ISOFS: unable to read i-node block
[17332959.264000] end_request: I/O error, dev sr0, sector 5156
[17332959.264000] ISOFS: unable to read i-node block
[17332959.268000] end_request: I/O error, dev sr0, sector 5224
[17332959.268000] ISOFS: unable to read i-node block
[17332959.272000] end_request: I/O error, dev sr0, sector 5236
[17332959.272000] ISOFS: unable to read i-node block
[17332959.276000] end_request: I/O error, dev sr0, sector 5244
[17332959.276000] ISOFS: unable to read i-node block
[17332959.280000] end_request: I/O error, dev sr0, sector 5256
[17332959.280000] ISOFS: unable to read i-node block
[17332959.284000] end_request: I/O error, dev sr0, sector 5268
[17332959.284000] ISOFS: unable to read i-node block
[17332959.288000] end_request: I/O error, dev sr0, sector 3360
[17332959.288000] ISOFS: unable to read i-node block
[17332959.292000] end_request: I/O error, dev sr0, sector 4392
[17332959.292000] ISOFS: unable to read i-node block
[17332959.296000] end_request: I/O error, dev sr0, sector 4632
[17332959.296000] ISOFS: unable to read i-node block
[17332959.300000] end_request: I/O error, dev sr0, sector 4948
[17332959.300000] ISOFS: unable to read i-node block
[17332959.304000] end_request: I/O error, dev sr0, sector 7440
[17332959.304000] Buffer I/O error on device sr0, logical block 1860
[17332959.304000] Buffer I/O error on device sr0, logical block 1861
[17332959.304000] Buffer I/O error on device sr0, logical block 1862
[17332959.304000] Buffer I/O error on device sr0, logical block 1863
[17332959.304000] Buffer I/O error on device sr0, logical block 1864
[17332959.304000] Buffer I/O error on device sr0, logical block 1865
[17332959.304000] Buffer I/O error on device sr0, logical block 1866
[17332959.304000] Buffer I/O error on device sr0, logical block 1867
[17332959.308000] end_request: I/O error, dev sr0, sector 7440
[17332959.308000] Buffer I/O error on device sr0, logical block 1860
[17332959.308000] Buffer I/O error on device sr0, logical block 1861
[17332959.312000] end_request: I/O error, dev sr0, sector 7440
[17332959.316000] end_request: I/O error, dev sr0, sector 5288
[17332959.316000] ISOFS: unable to read i-node block
[17332959.320000] end_request: I/O error, dev sr0, sector 5300
[17332959.320000] ISOFS: unable to read i-node block
[17332959.608000] end_request: I/O error, dev sr0, sector 7132
[17332959.616000] end_request: I/O error, dev sr0, sector 7132
[17332959.704000] end_request: I/O error, dev sr0, sector 7316
[17332959.708000] end_request: I/O error, dev sr0, sector 7316
[17332959.728000] end_request: I/O error, dev sr0, sector 7364
[17332959.732000] end_request: I/O error, dev sr0, sector 7364
[17332959.740000] end_request: I/O error, dev sr0, sector 7440
[17332959.744000] end_request: I/O error, dev sr0, sector 7472
[17332959.764000] end_request: I/O error, dev sr0, sector 7488
[17332959.768000] end_request: I/O error, dev sr0, sector 7488
[17332979.372000] cdrom: This disc doesn't have any tracks I recognize!
[17333132.208000] cdrom: This disc doesn't have any tracks I recognize!

```

This is running an up to date Ubuntu Edgy Eft install.

Any help/ideas?

---

