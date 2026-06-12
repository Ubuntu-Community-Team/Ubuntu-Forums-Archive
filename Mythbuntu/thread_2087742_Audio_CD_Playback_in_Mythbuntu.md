---
title: "Audio CD Playback in Mythbuntu"
date: 2012-11-24
forum: Mythbuntu
---

### Post by themoog on 2012-11-24
I can no longer play audio CDs in My Mythbuntu frontend.
 
Muthbuntu 12.04 with MythTV-fixes 0.25.3-15.
 
Strangely I can still rip CDs in MythTV and I can play them in the Ubuntu desktop (with Mythtv closed)  in the desktop they appear as a folder full of wav files.
 
Most importantly, I *can* play audio CDs in VLC, so this points to it being a problem with the way MythTV is accessing the cdrom.
 
Could it be that the desktop is getting in the way?
 
I say this, as in the frontend logs I see the following error:
E CoreContext dvdringbuffer.cpp:53 (DVDInfo) DVDInfo: Failed to open device at /dev/sr0

dmesg gets the errors, pasted below, repeated many times.
 
I've searched lots and found many instances of these errors in the past, but none of recent and none only in MythTV.  All updates, including Kernal are applied.
 
[  969.549355] sr 2:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  969.549363] sr 2:0:0:0: [sr0]  Sense Key : Illegal Request [current]
[  969.549368] Info fld=0x0
[  969.549372] sr 2:0:0:0: [sr0]  Add. Sense: Illegal mode for this track
[  969.549379] sr 2:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[  969.549394] end_request: I/O error, dev sr0, sector 0
[  969.549397] quiet_error: 8 callbacks suppressed
[  969.549402] Buffer I/O error on device sr0, logical block 0
[  969.549407] Buffer I/O error on device sr0, logical block 1
[  969.549412] Buffer I/O error on device sr0, logical block 2
[  969.549415] Buffer I/O error on device sr0, logical block 3
[  969.555207] sr 2:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  969.555212] sr 2:0:0:0: [sr0]  Sense Key : Illegal Request [current]
[  969.555216] Info fld=0x0
[  969.555218] sr 2:0:0:0: [sr0]  Add. Sense: Illegal mode for this track
[  969.555223] sr 2:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[  969.555232] end_request: I/O error, dev sr0, sector 0

---

