---
title: "DVD Not Playing"
date: 2011-06-26
forum: Multimedia Software
---

### Post by sandeep.prabhu on 2011-06-26
Im trying to play a DVD Movie on Ubuntu 10.10 using VLC Player. 
I get this on dmesg.

[88921.811917] end_request: I/O error, dev sr0, sector 180008
[88944.607462] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[88944.607470] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[88944.607475] sr 0:0:0:0: [sr0] Add. Sense: Read of scrambled sector without authentication
[88944.607485] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 01 c8 00 00 02 00
[88944.607495] end_request: I/O error, dev sr0, sector 1824
[88944.607501] quiet_error: 104 callbacks suppressed
[88944.607505] Buffer I/O error on device sr0, logical block 456
[88944.607510] Buffer I/O error on device sr0, logical block 457
[88944.611387] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[88944.611394] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[88944.611399] sr 0:0:0:0: [sr0] Add. Sense: Read of scrambled sector without authentication
[88944.611408] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 01 c8 00 00 02 00
[88944.611418] end_request: I/O error, dev sr0, sector 1824
[88944.611422] Buffer I/O error on device sr0, logical block 456
[88944.611426] Buffer I/O error on device sr0, logical block 457
[88944.853690] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[88944.853696] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[88944.853701] sr 0:0:0:0: [sr0] Add. Sense: Read of scrambled sector without authentication
[88944.853710] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 af ca 00 00 02 00
[88944.853720] end_request: I/O error, dev sr0, sector 180008
[88944.853725] Buffer I/O error on device sr0, logical block 45002
[88944.853729] Buffer I/O error on device sr0, logical block 45003
[88944.857678] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[88944.857683] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[88944.857688] sr 0:0:0:0: [sr0] Add. Sense: Read of scrambled sector without authentication
[88944.857695] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 af ca 00 00 02 00
[88944.857704] end_request: I/O error, dev sr0, sector 180008
[88944.857708] Buffer I/O error on device sr0, logical block 45002
[88944.857711] Buffer I/O error on device sr0, logical block 45003
[88944.880081] sr 0:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[88944.880088] sr 0:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[88944.880094] sr 0:0:0:0: [sr0] Add. Sense: Read of scrambled sector without authentication
[88944.880103] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 af ca 00 00 02 00
[88944.880114] end_request: I/O error, dev sr0, sector 180008
[88944.880121] Buffer I/O error on device sr0, logical block 45002
[88944.880125] Buffer I/O error on device sr0, logical block 45003


Tried playing with Totem Movie Player 2.32.0, it cannot find a suitable plugin.
"The requested plugins are:

DVD source".

---

### Post by jerrrys on 2011-06-26
got your lib's in order?

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

also i will have to assume that this is still true,  but if you download vlc from outside source.  you will get restricted drivers that ubuntu cannot supply because of copyright.  but like i said, don't know for sure, i research that about two years ago and things can change.

---

