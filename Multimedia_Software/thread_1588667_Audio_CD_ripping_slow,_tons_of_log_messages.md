---
title: "Audio CD ripping: slow, tons of log messages"
date: 2010-10-05
forum: Multimedia Software
---

### Post by karsten_df on 2010-10-05
hi,

I have a problem which looks quite similar to post #1576314 ([http://ubuntuforums.org/showthread.php?t=1576314](http://ubuntuforums.org/showthread.php?t=1576314)) - the obvious difference being that #1576314 is marked as solved with kernel 2.6.32.25, which is exactly the kernel I appear to use.

Configuration:
- ubuntu server 10.04.01 on an amd64 based micro server 
  (should be up to date as of 2010-10-5)
- halevt, abcde installed for automated audio CD ripping from SATA DVD-RW drive sr0

The problem:
- CD ripping seems unexpectedly slow (while DMA seems configured)
- loads of log messages of the kind
[12048.461772] sr 4:0:1:0: [sr0] Add. Sense: Illegal mode for this track
[12048.461784] sr 4:0:1:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[12048.461800] end_request: I/O error, dev sr0, sector 0
[12048.466934] sr 4:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[12048.466945] sr 4:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[12048.466955] Info fld=0x0, ILI
(apart from the last line, the log output seems identical to the one in described in #1576314)

Not sure if the warnings point to an issue which is also causing the slow CD read progress, but it seems possible to me at least ;-)

Does anybody have a similar problem, or even have an idea what to do about it?

regards -

Karsten

---

