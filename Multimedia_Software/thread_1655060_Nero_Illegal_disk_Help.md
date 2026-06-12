---
title: "Nero Illegal disk???? Help"
date: 2010-12-29
forum: Multimedia Software
---

### Post by blazer2010 on 2010-12-29
Here's my nero report log, I just bought some dvd blanks & they're not working. Am using my laptop Dell Inspiron 1525 burner, it takes abit of time to recognise itthen i only have 2 options of burn speed 3x & 4x yet i normally burn at 6x & 8x. Please help!
 
```
Windows Vista 6.0
IA32
WinAspi: -
NT-SPTI used
Nero Version: 10.0.10.100
Internal Version: 10,0,10,100
(Nero Express)
Recorder: <TSSTcorp DVD+-RW TS-L632H>Version: DW30 - HA 1 TA 0 - 10.0.10.100
Adapter driver: <Serial ATA> HA 1
Drive buffer : 2048kB
Bus Type : via Inquiry data
CD-ROM: <ODSFYFU 05YBCLQJ09 >Version: 1.04 - HA 1 TA 1 - 10.0.10.100
Adapter driver: <IDE> HA 1
=== Scsi-Device-Map ===
CdRomPeripheral : ODSFYFU 05YBCLQJ09 1.04 a3wvti76 Port 4 ID 0 DMA: Off
=== CDRom-Device-Map ===
TSSTcorp DVD+-RW TS-L632H D: CdRom0
ODSFYFU 05YBCLQJ09 E: CdRom1
=======================
AutoRun : 1
Excluded drive IDs: 
WriteBufferSize: 83886080 (0) Byte
BUFE : 0
Physical memory : 2047MB (2097151kB)
Free physical memory: 1289MB (1320392kB)
Memory in use : 57 %
Uncached PFiles: 0x0
Global Bus Type: default (0)
Check supported media : Disabled (0) 
29.12.2010
UDF/ISO compilation
12:21:41 #1 Text 0 File SCSIPTICommands.cpp, Line 464
LockMCN - completed sucessfully for IOCTL_STORAGE_MCN_CONTROL
 
12:21:41 #2 PHASE 114 File dlgbrnst.cpp, Line 1827
DVD-Video files reallocation completed (no file modified)
 
12:21:41 #3 Text 0 File Isodoc.cpp, Line 6956
UDF document burn settings
------------------------------------------
Determine maximum speed : FALSE
Simulate : FALSE
Write : TRUE
Finalize CD : TRUE
Multisession : FALSE
Burning mode : DAO
Mode : 1
UDF Mode : UDF/ISO bridge
UDF Options : automatic
UDF Revision : 1.02
UDF Partition Type : physical
ISO Level : 1 (Max. of 11 = 8 + 3 char)
Character set : ISO 9660
Joliet : FALSE
Allow pathdepth more than 8 directories : FALSE
Allow more than 255 characters in path : FALSE
Write ISO9660 ;1 file extensions : TRUE
 
12:21:41 #4 PHASE 111 File dlgbrnst.cpp, Line 1827
DVD-Video files sorted
 
12:21:42 #5 ISO9660GEN -11 File Geniso.cpp, Line 3336
First writeable address = 0 (0x00000000)
 
12:21:42 #6 Text 0 File compose.cpp, Line 874
GenUDF2: 1 transfer items prepared.
 
12:21:42 #7 ISO9660GEN -11 File Geniso.cpp, Line 3336
First writeable address = 0 (0x00000000)
 
12:21:42 #8 Text 0 File Burncd.cpp, Line 3568
Turn on Disc-At-Once, using DVD media
 
12:21:42 #9 Text 0 File DlgWaitCD.cpp, Line 314
[D: DVD+-RW TS-L632H] Last possible write address on media: 16645887
Last address to be written: 1945183
 
12:21:42 #10 Text 0 File DlgWaitCD.cpp, Line 326
[D: DVD+-RW TS-L632H] Write in overburning mode: NO (enabled: CD)
 
12:21:42 #11 Text 0 File DlgWaitCD.cpp, Line 2890
Recorder: TSSTcorp DVD+-RW TS-L632H, Media type: DVD+RW
Disc Manufacturer ID: <0dz¶Èª„>, Media Type ID: <ˆŠ>, Product revision number: 7
Disc Application Code: 139, Extended Information Indicators: 152
 
12:21:42 #12 Text 0 File DlgWaitCD.cpp, Line 499
[D: DVD+-RW TS-L632H] >>> Protocol of DlgWaitCD activities: <<<
=========================================
 
12:21:42 #13 Text 0 File ThreadedTransferInterface.cpp, Line 785
Setup items (after recorder preparation)
0: TRM_DATA_MODE1 ()
2 indices, index0 (150) not provided
original disc pos #0 + 1945184 (1945184) = #1945184/432:15.59
relocatable, disc pos for caching/writing not required/ required
-> TRM_DATA_MODE1, 2048, config 0, wanted index0 0 blocks, length 1945184 blocks [D: TSSTcorp DVD+-RW TS-L632H]
--------------------------------------------------------------
 
12:21:42 #14 Text 0 File ThreadedTransferInterface.cpp, Line 1001
Prepare [D: TSSTcorp DVD+-RW TS-L632H] for write in CUE-sheet-DAO
DAO infos:
==========
MCN: ""
TOCType: 0x00; Session Closed, disc fixated
Tracks 1 to 1: Idx 0 Idx 1 Next Trk
1: TRM_DATA_MODE1, 2048/0x00, FilePos 0 0 3983736832, ISRC ""
DAO layout:
===========
___Start_|____Track_|_Idx_|_CtrlAdr_|_____Size_|______NWA_|_RecDep__________
0 | lead-in | 0 | 0x41 | 0 | 0 | 0x00
0 | 1 | 0 | 0x41 | 0 | 0 | 0x00
0 | 1 | 1 | 0x41 | 1945184 | 0 | 0x00
1945184 | lead-out | 1 | 0x41 | 0 | 0 | 0x00
MediaType: DVD+RW
 
12:21:42 #15 Text 0 File SCSIPTICommands.cpp, Line 251
SPTILockVolume - completed successfully for FSCTL_LOCK_VOLUME
 
12:21:42 #16 Text 0 File Burncd.cpp, Line 4278
Caching options: cache CDRom or Network-Yes, small files-No (<64KB)
 
12:21:42 #17 PHASE 24 File dlgbrnst.cpp, Line 1827
Caching of files started
 
12:21:42 #18 Text 0 File Burncd.cpp, Line 4400
Cache writing successful.
 
12:21:42 #19 PHASE 25 File dlgbrnst.cpp, Line 1827
Caching of files completed
 
12:21:42 #20 Text 0 File Burncd.cpp, Line 498
Advanced Automatic Write Strategy (A-AWS) is supported. Current status is disabled
 
12:21:42 #21 PHASE 36 File dlgbrnst.cpp, Line 1827
Burn process started at 4x (5,540 KB/s)
 
12:21:42 #22 Text 0 File ThreadedTransferInterface.cpp, Line 2769
Verifying disc position of item 0 (relocatable, disc pos, no patch infos, orig at #0): write at #0
 
12:21:42 #23 Text 0 File Cdrdrv.cpp, Line 10559
---- Disc Structure: Physical Format Information (00h) ----
Media Type: 0, Layer: 0, Address: 0 (0 h), AGID: 0; Length: 2050
Book Type: DVD-ROM (0), Part Version: 1.9x (4)
Disc Size: 120 mm, Maximum Transfer Rate: 10,08 Mbps (2 h)
Number of Layers: 4, Track Path: Opposite Track Path (OTP), Layer Type: ?
Linear Density: 0,267 um/bit, Track Density: 0,74 um/track
Starting Physical Sector Number of Data Area: 740000 h (?)
End Physical Sector Number of Data Area: 0 h
Data in Burst Cutting Area (BCA) does not exist
Twin Format Flag: 1
DVD-Download media, Disc Identifier:
Disc Indicator: 7 h, Major Digit of Revision Number: A h
Media Specific [16..783]:
04 8B 98 02 30 64 7A B6 - C8 AA 84 05 88 8A 07 36 ....0dz........6
CE F6 CB F8 E8 E4 CC 40 - 10 82 31 42 4A CF 32 32 .......@..1BJ.22
1C 05 47 58 6E FD 02 5A - 4F FD 60 56 CA 74 DA 72 ..GXn..ZO.`V.t.r
FA BA A2 21 00 62 0C 85 - 89 BA 24 30 CE 78 53 FA ...!.b....$0.xS.
D8 AE A4 89 D8 28 B5 47 - C2 77 CA 16 D6 F7 73 00 .....(.G.w....s.
86 11 CE 1A 5F 7F 51 14 - 80 B9 16 50 E6 BD 1A D9 ...._.Q....P....
6E 9F 0E DF C6 47 44 66 - 04 0C 89 88 22 14 06 A8 n....GDf...."...
D8 4A B9 C2 4B CD EE 26 - 18 8F 20 FA 5E BF 6A 93 .J..K..&....^.j.
87 57 E4 53 42 CE DC 46 - 30 4A 69 D9 E8 8E C0 C5 .W.SB..F0Ji.....
99 38 15 72 84 B5 9F D8 - C4 A9 1C 71 C0 87 6A 1C .8.r.......q..j.
77 13 3E 67 CB 1E B6 D5 - B7 1D 8D 8A AA 40 1C 83 w.>g.........@..
A9 72 7C AB 6C 3B 5F 1D - 5D 91 09 03 32 60 28 C5 .r|.l;_.]...2`(.
49 23 B6 31 AA 56 1E 6F - F1 21 C6 7B 43 9E F4 E3 I#.1.V.o.!.{C...
75 A8 5E 5B 77 D8 14 B2 - BF 32 98 36 36 AA B8 02 u.^[w....2.66...
70 4A E9 C8 EA 8C 84 89 - 98 20 34 46 E0 51 CA 9A pJ........4F.Q..
C6 6D 41 72 AC B0 CF 78 - 71 FE DC 26 3C 8B E8 6A .mAr...xq..&<..j
DD 8E 0A DD 4E 13 5E 4D - 75 34 4C E1 05 E2 B7 93 ....N.^Mu4L.....
9D 54 90 3B 27 12 AC 70 - D6 FB 72 98 B6 27 A8 BA .T.;'..p..r..'..
46 3C 4B F1 E9 DE E8 60 - DC DA 22 F0 1B E3 4B AF F<K....`.."...K.
E2 A3 91 35 04 CA 90 C7 - 39 69 5F F9 40 DA 9A E6 ...5....9i_.@...
69 01 F2 3D A3 CF 3E 79 - B3 C5 1F 29 DB 68 DB CA i..=..>y...).h..
CE CC D3 B1 F1 65 9E CB - 68 3A 08 84 44 10 0A 21 .....e..h:..D..!
50 68 AD C4 E3 15 A4 9F - DA C4 ED 14 78 A7 E5 B3 Ph..........x...
7D 09 5B 39 D1 49 8B A2 - 63 08 A7 05 AE BE 8A AC }.[9.I..c.......
40 D0 9B B2 41 2C A7 CD - B6 2D A9 EE 6E 11 1E 01 @...A,...-..n...
FC 3C 7F F7 01 0E 23 D8 - 3C B7 EF 92 2D 61 F6 FD .<....#.<...-a..
32 5C 2F 3D B9 CC 4A 11 - D6 19 6F 1F 3D D9 C0 8B 2\/=..J...o.=...
90 65 2C 6F D5 25 0E EB - C0 AF 94 AD BC EC E4 45 .e,o.%.........E
40 22 84 15 8A 9A 46 7C - 43 70 E8 FC CE 60 50 CA @"....F|Cp...`P.
B8 C2 69 C9 EA AE 80 8D - 10 B8 36 76 A2 39 03 52 ..i.......6v.9.R
6C E9 44 FA 16 B6 FB B2 - 81 35 24 CE D0 47 A8 7A l.D......5$..G.z
5F BF 48 97 83 DF 7C 51 - 72 8C B4 8F F8 E0 ED DC _.H...|Qr.......
60 34 C6 F1 53 C8 DE 8A - E9 47 B5 11 E7 29 42 92 `4..S....G...)B.
E1 D5 6C 59 53 98 D4 2B - 2D 33 E9 18 7B 3F 91 8D ..lYS..+-3..{?..
12 B8 72 7E AB 28 33 56 - 0C 6D 94 29 46 1E 6D 61 ..r~.(3V.m.)F.ma
C2 41 2A 11 4B B7 A7 11 - 0E 66 D3 45 EB 8F 5B 9E .A*.K....f.E..[.
A0 17 28 FB F5 EF 9C 2C - BD CE C7 CD 4C 32 1E 27 ..(....,....L2.'
FA B0 E1 75 33 4F F1 EB - 7C DC 65 BC 02 F9 5A D9 ...u3O..|.e...Z.
EE 8E 04 DE 95 01 4E 77 - 27 38 E4 FA 72 5A 0F 0C ......Nw'8..rZ..
85 49 A9 A7 33 A8 12 52 - 7E E9 0B F6 02 B0 73 3E .I..3..R~.....s>
94 B1 F9 D4 ED 8A 21 71 - 5E CB 49 FE 16 EE EB A0 ......!q^.I.....
A3 55 22 06 FD D3 A0 71 - EB AF 51 E5 7C E0 B6 F3 .U"....q..Q.|...
04 A3 47 A4 CF D1 E9 9E - 6C F1 DE DA 64 F8 56 FA ..G.....l...d.V.
72 BA A0 2A 11 19 77 27 - 14 99 33 46 5F CF CF 67 r..*..w'..3F_..g
36 D9 0D 59 4B BD 1C 8E - C6 C5 2D F6 3B A1 3F 64 6..YK.....-.;.?d
1E 4B 79 F9 51 DA 12 F6 - 7B 23 92 35 62 C6 9D 5E .Ky.Q...{#.5b..^
91 6F 0F 3F F9 80 C3 19 - E5 0F 6B F3 A9 92 61 68 .o.?......k...ah
EF CC 26 1C 8F A8 EA 4C - 9D 0A 9B 46 5E 47 74 60 ..&....L...F^Gt`
 
12:21:42 #24 PHASE 98 File dlgbrnst.cpp, Line 1827
Start formatting disc before burning
 
12:21:42 #25 SPTI -1046 File SCSIPassThrough.cpp, Line 217
CdRom0: SCSIStatus(x02) WinError(0) NeroError(-1046)
CDB Data: 0x04 11 00 00 00 00 00 00 00 00 00 00 
Sense Key: 0x05 (KEY_ILLEGAL_REQUEST)
Sense Code: 0x30
Sense Qual: 0x06
Sense Area: 0x70 00 05 00 00 00 00 0A 00 00 00 00 30 06 
Buffer x04778dc0: Len xc
0x00 82 00 08 00 FD FF 00 98 00 00 00 
 
12:21:42 #26 PHASE 101 File dlgbrnst.cpp, Line 1827
Formatting disc failed
 
12:21:42 #27 Text 0 File DVDPlusRW.cpp, Line 637
Start write address at LBA 0
DVD high compatibility mode: Yes
 
12:21:42 #28 CDR -1046 File ThreadedTransferInterface.cpp, Line 1776
Illegal disc
D: TSSTcorp DVD+-RW TS-L632H
 
12:21:42 #29 TRANSFER -27 File ThreadedTransfer.cpp, Line 1222
Could not perform start of Disc-at-once
 
12:21:42 #30 Text 0 File DVDPlusDualLayer.cpp, Line 1460
SetDriveCaps: Set LAST LBA of layer 1 to 0
 
12:21:42 #31 Text 0 File ThreadedTransfer.cpp, Line 273
Pipe memory size 83836800
 
12:21:43 #32 PHASE 38 File dlgbrnst.cpp, Line 1827
Burn process failed at 4x (5,540 KB/s)
 
12:21:43 #33 Text 0 File SCSIPTICommands.cpp, Line 301
SPTIDismountVolume - completed successfully for FSCTL_DISMOUNT_VOLUME
 
12:21:43 #34 Text 0 File Cdrdrv.cpp, Line 11916
DriveLocker: UnLockVolume completed
 
12:21:43 #35 Text 0 File SCSIPTICommands.cpp, Line 464
UnLockMCN - completed sucessfully for IOCTL_STORAGE_MCN_CONTROL
 
Existing drivers:
Registry Keys:
HKLM\Software\Microsoft\Windows NT\CurrentVersion\WinLogon
```

---

### Post by cascade9 on 2010-12-29
This isnt really much of a windows forum, I doubt anybody is going to help much with that. 

I'd guess that you've bought 4x DVDs if you've been able to burn at 6-8x in the past.

---

### Post by blazer2010 on 2010-12-29
Sorry about that didn't realise. There 8x 4sure, tried looking around couldn't find a solution. Was hoping some1 could look through my log and see if its a fault i can sort out. Already asked a couple of mates & they say its the blanks, apparently got a bad pack or something... only problem is they're a spindle tab of 50... if worse comes 2 worse, will take them back and exchange for another type of blanks (if they allow to, bought them 2days ago & still have receipt)... fingers crossed! :lolflag:

---

### Post by howefield on 2010-12-29
Thread closed.

This being an Ubuntu support forum, your question would be better asked elsewhere.

If you are using Ubuntu and need some support, please start a new thread.

---

