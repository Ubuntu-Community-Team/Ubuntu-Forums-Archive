---
title: "old cd's not being read in kubuntu"
date: 2014-08-08
forum: Multimedia Software
---

### Post by nonparity on 2014-08-08
Some older cd's are not being read by Kubuntu. It just does not recognize them at all. I have a dual os install of Kubuntu and Ubuntu. On the standard Ubuntu install it reads these fine but Kubuntu is not. 

I purchased a few cd's and noticed an old one was not being read. I had it replaced and the same issue happened again so this time I dug out some other old ones and the same thing happens with most of those. but all newer cd's(like 10 years or less) are fine.

Here is from dmesg

[689888.295439] Read(10): 28 00 00 03 6f 44 00 00 02 00
[689888.295443] end_request: I/O error, dev sr1, sector 900368
[689888.295446] Buffer I/O error on device sr1, logical block 225092
[689888.295449] Buffer I/O error on device sr1, logical block 225093
[689891.539178] sr 1:0:1:0: [sr1]  
[689891.539182] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[689891.539184] sr 1:0:1:0: [sr1]  
[689891.539185] Sense Key : Illegal Request [current] 
[689891.539188] sr 1:0:1:0: [sr1]  
[689891.539191] Add. Sense: Illegal mode for this track
[689891.539193] sr 1:0:1:0: [sr1] CDB: 
[689891.539194] Read(10): 28 00 00 03 6f 44 00 00 02 00
[689891.539200] end_request: I/O error, dev sr1, sector 900368
[689891.539203] Buffer I/O error on device sr1, logical block 225092
[689891.539206] Buffer I/O error on device sr1, logical block 225093
[689894.786518] sr 1:0:1:0: [sr1]  
[689894.786522] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[689894.786523] sr 1:0:1:0: [sr1]  
[689894.786524] Sense Key : Illegal Request [current] 
[689894.786526] sr 1:0:1:0: [sr1]  
[689894.786529] Add. Sense: Illegal mode for this track
[689894.786530] sr 1:0:1:0: [sr1] CDB: 
[689894.786531] Read(10): 28 00 00 03 6f 44 00 00 02 00
[689894.786535] end_request: I/O error, dev sr1, sector 900368
[689894.786539] Buffer I/O error on device sr1, logical block 225092
[689894.786541] Buffer I/O error on device sr1, logical block 225093


Any help with this would be great. It has me stumped why it works in Ubuntu but not Kubuntu.

---

