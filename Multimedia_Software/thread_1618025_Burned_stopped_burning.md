---
title: "Burned stopped burning"
date: 2010-11-10
forum: Multimedia Software
---

### Post by Voorhees1979 on 2010-11-10
Hey guys

My burner has stopped burning, it seems to burn the first part of the disc then stops, no matter what program I use to burn. I have attached a log from nero linux:

```
9M1K-0098-P3HL-PK6P-T6UA-1E5X-****-****

Linux (Ubuntu 10.04 'lucid') 2.6.32-25-generic (i686)
Nero API version: 9.7.0.132
Using interface version: 9.0.1.4
Installed in: /usr/lib/nero/
Application: Nero AG\Nero Linux
Internal Version: 9, 7, 0, 132

Recorder:             <PIONEER DVD-RW  DVR-116D>Version: 1.09 - HA 1 TA 0 - 0.0.0.0
 Adapter driver:      <ata_piix>                HA 1
 Drive buffer  :      2000kB
 Bus Type      :      via Inquiry data
Excluded drive IDs: 
WriteBufferSize: 83886080 (0) Byte
BUFE           : 0
Physical memory     : 1507MB (1544008kB)
Free physical memory: 113MB (115756kB)
Memory in use       : 92 %
Uncached PFiles: 0x0
Global Bus Type: default (0)
Check supported media : Disabled (0) 

10.11.2010
NeroAPI
08:57:40	#1 Text 0 File Burncd.cpp, Line 3647
	Turn on Disc-At-Once, using DVD media
	
08:57:41	#2 Text 0 File DlgWaitCD.cpp, Line 313
	Last possible write address on media:  2298495
	Last address to be written:            2201279
	
08:57:41	#3 Text 0 File DlgWaitCD.cpp, Line 325
	Write in overburning mode: NO
	
08:57:41	#4 Text 0 File DlgWaitCD.cpp, Line 2856
	Recorder: PIONEER DVD-RW  DVR-116D, Media type: DVD-R
	 Disc Manufacturer ID: <RITEKG> <05>
	 Disc Application Code: 64, Disc Physical Code: 193
	
08:57:41	#5 Text 0 File DlgWaitCD.cpp, Line 500
	>>> Protocol of DlgWaitCD activities: <<<
	=========================================
	
08:57:41	#6 Text 0 File ThreadedTransferInterface.cpp, Line 734
	Setup items (after recorder preparation)
	 0: TRM_DATA_MODE1 (2 - CD-ROM Mode 1, ISO 9660)
	    2 indices, index0 (150) not provided
	    original disc pos #0 + 2201280 (2201280) = #2201280/489:10.30
	    not relocatable, disc pos for caching/writing not required/not required
	    -> TRM_DATA_MODE1, 2048, config 0, wanted index0 0 blocks, length 2201280 blocks [PIONEER DVD-RW  DVR-116D (H:1 T:0)]
	--------------------------------------------------------------
	
08:57:41	#7 Text 0 File ThreadedTransferInterface.cpp, Line 936
	Prepare [PIONEER DVD-RW  DVR-116D (H:1 T:0)] for write in CUE-sheet-DAO
	DAO infos:
	==========
	 MCN: ""
	 TOCType: 0x00; Session Closed, disc fixated
	 Tracks 1 to 1:                                  Idx 0         Idx 1      Next Trk
	   1: TRM_DATA_MODE1, 2048/0x00, FilePos             0             0    4508221440, ISRC ""
	DAO layout:
	===========
	 ___Start_|____Track_|_Idx_|_CtrlAdr_|_____Size_|______NWA_|_RecDep__________
	        0 |  lead-in |   0 |    0x41 |        0 |        0 | 0x00
	        0 |        1 |   0 |    0x41 |        0 |        0 | 0x00
	        0 |        1 |   1 |    0x41 |  2201280 |  2201280 | 0x00
	  2201280 | lead-out |   1 |    0x41 |        0 |        0 | 0x00
	
08:57:41	#8 Text 0 File Burncd.cpp, Line 4354
	Caching options: cache CDRom or Network-No, small files-Yes (<32KB)
	
08:57:41	#9 Phase 24 File ExtendedProgress.cpp, Line 537
	Caching of files started
	
08:57:41	#10 Text 0 File Burncd.cpp, Line 4476
	Cache writing successful.
	
08:57:41	#11 Phase 25 File ExtendedProgress.cpp, Line 537
	Caching of files completed
	
08:57:41	#12 Phase 36 File ExtendedProgress.cpp, Line 537
	Burn process started at 8x (11080 KB/s)
	
08:57:41	#13 Text 0 File ThreadedTransferInterface.cpp, Line 2690
	Verifying disc position of item 0 (not relocatable, no disc pos, no patch infos, orig at #0): write at #0
	
08:57:42	#14 Text 0 File DVDR.cpp, Line 3287
	Recording mode: Sequential Recording Mode
	
08:57:42	#15 Text 0 File DVDR.cpp, Line 3441
	Start write address at LBA 0
	DVD high compatibility mode: Yes
	
08:57:42	#16 SCSI -1066 File SCSIInterface.cpp, Line 367
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xb6a01040
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x05 (0x0B, SCSI_TASTATUS_FAILED)
	Sense Key:  0x05 (KEY_ILLEGAL_REQUEST)
	Sense Code: 0x24
	Sense Qual: 0x00
	CDB Data:   0xAC 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x64 0x00 0x00 
	Sense Data: 0x70 0x00 0x05 0x00 0x00 0x00 0x00 0x0E 
	            0x00 0x00 0x00 0x00 0x24 0x00 
	
08:57:42	#17 Text 0 File Cdrdrv.cpp, Line 10169
	---- Disc Structure: Physical Format Information (00h) ----
	Media Type: 0, Layer: 0, Address: 0 (0 h), AGID: 0; Length: 2050
	 Book Type: DVD-R (2), Part Version: 2.0x (5), Extended Part Version: 0.0 (0)
	 Disc Size: 120 mm,      Maximum Transfer Rate: <not specified> (F h)
	 Number of Layers: 1,    Track Path: Parallel Track Path (PTP),  Layer Type: recordable
	 Linear Density:         0,267 um/bit,  Track Density:  0,74 um/track
	 Starting Physical Sector Number of Data Area: 30000 h (DVD-ROM, DVD-R/-RW, DVD+R/+RW)
	 Outer Limit of Data Recordable Area:          0 h
	 Data in Burst Cutting Area (BCA) does not exist
	  Revision number of maximum recording speed: 3.0
	  Revision number of minimum recording speed: 0.0
	  Revision number table of recording speed: 0.1 0.2 0.3 - - - 0.4 
	  Class: 0,  Extended part version: 0
	  Start PSN of the Extra Border Zone: 0 h
	  Start PSN of Physical format information blocks in Extra Border Zone: 0 h
	 Media Specific [16..783]:
	    00 30 01 02 04 06 00 00 - 00 08 00 00 00 00 00 00    .0..............
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    15 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    01 40 C1 FD 9E D8 52 00 - 02 B6 0E 11 98 9A 80 00    .@....R.........
	    03 52 49 54 45 4B 47 00 - 04 30 35 00 00 00 00 00    .RITEKG..05.....
	    05 88 80 00 00 00 02 00 - 06 08 12 11 98 9A 80 00    ................
	    07 88 80 00 00 00 00 00 - 08 03 17 0A 0B 09 02 00    ................
	    09 96 05 0C 0B 60 00 00 - 0A 00 00 00 00 00 10 00    .....`..........
	    0B 04 1D 17 B8 88 75 00 - 0C 89 AC 98 81 00 10 00    ......u.........
	    0D 00 00 D0 00 00 00 00 - 0E 09 24 37 2F 29 1E 00    ..........$7/)..
	    0F 50 17 27 19 89 B5 00 - 10 88 84 00 04 00 04 00    .P.'............
	    11 00 00 00 00 00 00 00 - 12 09 31 3B 33 2B 1D 00    ..........1;3+..
	    13 50 1D 2B 1F 97 B5 00 - 14 88 84 00 04 00 04 00    .P.+............
	    15 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	    00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
	
08:57:42	#18 Text 0 File DVDR.cpp, Line 3579
	Reserved Track size: 2201280 (2196C0h, 4299MB) -> return code 0
	
08:57:42	#19 Text 0 File ThreadedTransfer.cpp, Line 273
	Pipe memory size 83836800
	
08:57:42	#20 Text 0 File Cdrdrv.cpp, Line 1273
	08:57:42 - PIONEER DVD-RW  DVR-116D (H:1 T:0) : Queue again later
	
08:58:08	#21 Text 0 File Cdrdrv.cpp, Line 1273
	08:58:08 - PIONEER DVD-RW  DVR-116D (H:1 T:0) : Queue again later
	
08:58:09	#22 Text 0 File Cdrdrv.cpp, Line 1273
	08:58:09 - PIONEER DVD-RW  DVR-116D (H:1 T:0) : Queue again later
	
08:58:09	#23 Text 0 File Cdrdrv.cpp, Line 1273
	08:58:09 - PIONEER DVD-RW  DVR-116D (H:1 T:0) : Queue again later
	
08:58:09	#24 Text 0 File Cdrdrv.cpp, Line 1273
	08:58:09 - PIONEER DVD-RW  DVR-116D (H:1 T:0) : Queue again later
	
08:58:09	#25 Text 0 File Cdrdrv.cpp, Line 1273
	08:58:09 - PIONEER DVD-RW  DVR-116D (H:1 T:0) : Queue again later
	
08:58:09	#26 Text 0 File Cdrdrv.cpp, Line 1273
	08:58:09 - PIONEER DVD-RW  DVR-116D (H:1 T:0) : Queue again later
	
08:58:09	#27 Text 0 File Cdrdrv.cpp, Line 1273
	08:58:09 - PIONEER DVD-RW  DVR-116D (H:1 T:0) : Queue again later
	
08:58:09	#28 Text 0 File Cdrdrv.cpp, Line 1273
	08:58:09 - PIONEER DVD-RW  DVR-116D (H:1 T:0) : Queue again later
	
08:58:09	#29 Text 0 File Cdrdrv.cpp, Line 1273
	08:58:09 - PIONEER DVD-RW  DVR-116D (H:1 T:0) : Queue again later
	
08:58:09	#30 Text 0 File Cdrdrv.cpp, Line 1273
	08:58:09 - PIONEER DVD-RW  DVR-116D (H:1 T:0) : Queue again later
	
08:58:09	#31 Text 0 File Cdrdrv.cpp, Line 1273
	08:58:09 - PIONEER DVD-RW  DVR-116D (H:1 T:0) : Queue again later
	
08:58:09	#32 Text 0 File Cdrdrv.cpp, Line 1273
	08:58:09 - PIONEER DVD-RW  DVR-116D (H:1 T:0) : Queue again later
	
08:58:09	#33 Text 0 File Cdrdrv.cpp, Line 1273
	08:58:09 - PIONEER DVD-RW  DVR-116D (H:1 T:0) : Queue again later
	
08:58:09	#34 Text 0 File Cdrdrv.cpp, Line 1273
	08:58:09 - PIONEER DVD-RW  DVR-116D (H:1 T:0) : Queue again later
	
08:58:09	#35 Text 0 File Cdrdrv.cpp, Line 1273
	08:58:09 - PIONEER DVD-RW  DVR-116D (H:1 T:0) : Queue again later
	
08:58:09	#36 Text 0 File Cdrdrv.cpp, Line 1273
	08:58:09 - PIONEER DVD-RW  DVR-116D (H:1 T:0) : Queue again later
	
08:58:09	#37 Text 0 File Cdrdrv.cpp, Line 1273
	08:58:09 - PIONEER DVD-RW  DVR-116D (H:1 T:0) : Queue again later
	
08:58:09	#38 Text 0 File Cdrdrv.cpp, Line 1273
	08:58:09 - PIONEER DVD-RW  DVR-116D (H:1 T:0) : Queue again later
	
08:58:09	#39 Text 0 File Cdrdrv.cpp, Line 1273
	08:58:09 - PIONEER DVD-RW  DVR-116D (H:1 T:0) : Queue again later
	
08:58:09	#40 Text 0 File Cdrdrv.cpp, Line 1273
	08:58:09 - PIONEER DVD-RW  DVR-116D (H:1 T:0) : Queue again later
	
08:58:09	#41 Text 0 File Cdrdrv.cpp, Line 1273
	08:58:09 - PIONEER DVD-RW  DVR-116D (H:1 T:0) : Queue again later
	
08:58:09	#42 Text 0 File Cdrdrv.cpp, Line 1273
	08:58:09 - PIONEER DVD-RW  DVR-116D (H:1 T:0) : Queue again later
	
08:58:09	#43 SCSI -400 File SCSIInterface.cpp, Line 624
	SCSI Exec, HA 1, TA 0, LUN 0, buffer 0x0xadfd0b80
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x05 (0x0B, SCSI_TASTATUS_FAILED)
	Sense Key:  0x05 (KEY_ILLEGAL_REQUEST)
	Sense Code: 0xA8
	Sense Qual: 0x03
	CDB Data:   0x2A 0x00 0x00 0x00 0x0D 0xA0 0x00 0x00 0x20 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x05 0x04 0x93 0x00 0x00 0x0E 
	            0x26 0x08 0x10 0xFE 0xA8 0x03 
	
08:58:09	#44 CDR -400 File Writer.cpp, Line 306
	Unspecified target error
	PIONEER DVD-RW  DVR-116D (H:1 T:0)
	
08:58:11	#45 Text 0 File DVDR.cpp, Line 3846
	EndDAO: Last written address was 3487 (D9Fh)
	
08:58:11	#46 Text 0 File DVDPlusDualLayer.cpp, Line 1455
	SetDriveCaps: Set LAST LBA of layer 1 to 0
	
08:58:11	#47 Phase 38 File ExtendedProgress.cpp, Line 537
	Burn process failed at 8x (11080 KB/s)
```

Any help would be great, drive seems to burn fine in XP, cheers

---

