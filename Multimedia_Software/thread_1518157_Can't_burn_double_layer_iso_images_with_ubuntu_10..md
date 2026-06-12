---
title: "Can't burn double layer iso images with ubuntu 10.04"
date: 2010-06-26
forum: Multimedia Software
---

### Post by felipebalbi on 2010-06-26
Hi,

I'm trying to burn a double layer iso image with growisofs on an eeebox 1501U. The dvd burner is a hitachi ga10n and the media I'm using is a maxell one.

From what I understood looking at dmesg, the dvd doesn't respond (or responds with error) to some specific commands sent by growisofs (actually kernel driver) then the kernel resets the device, which causes /dev/sr0 to disappear and makes the burning process fail.

Here's output from growisofs:

$ growisofs -use-the-force-luke=dao -use-the-force-luke=break:1913760 -dvd-compat -speed=2 -Z /dev/dvd=image.iso 
WARNING: /dev/dvd already carries isofs!
About to execute 'builtin_dd if=image.iso of=/dev/dvd obs=32k seek=0'
:-? L0 Data Zone Capacity is set already
/dev/dvd: "Current Write Speed" is 2.5x1352KBps.
:-? resuming track#1 from LBA#455200
  526385152/7838695424 ( 6.7%) @56.1x, remaining 1:23 RBU   0.0% UBU   0.0%
  796917760/7838695424 (10.2%) @58.6x, remaining 1:28 RBU   0.1% UBU   0.0%
:-[ WRITE@LBA=6f440h failed with SK=4h/TRACKING SERVO FAILURE]: Input/output error
:-( write failed: Input/output error


and from dmesg:

...

[388151.064455] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[388151.064463] Info fld=0x0
[388151.064467] sr 1:0:0:0: [sr0] Add. Sense: Logical block address out of range
[388151.064477] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[388151.064495] end_request: I/O error, dev sr0, sector 0
[388151.066779] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[388151.066787] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[388151.066796] Info fld=0x0
[388151.066800] sr 1:0:0:0: [sr0] Add. Sense: Logical block address out of range
[388151.066809] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[388151.066827] end_request: I/O error, dev sr0, sector 0
[388151.069108] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[388151.069117] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[388151.069126] Info fld=0x2
[388151.069130] sr 1:0:0:0: [sr0] Add. Sense: Logical block address out of range
[388151.069140] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 02 00 00 02 00
[388151.069157] end_request: I/O error, dev sr0, sector 8
[388151.071464] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[388151.071472] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[388151.071480] Info fld=0x20
[388151.071484] sr 1:0:0:0: [sr0] Add. Sense: Logical block address out of range
[388151.071494] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 20 00 00 02 00
[388151.071512] end_request: I/O error, dev sr0, sector 128
[388151.073767] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[388151.073777] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[388151.073786] Info fld=0x0
[388151.073790] sr 1:0:0:0: [sr0] Add. Sense: Logical block address out of range
[388151.073800] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[388151.073818] end_request: I/O error, dev sr0, sector 0
[388151.075854] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[388151.075862] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[388151.075871] Info fld=0x0
[388151.075875] sr 1:0:0:0: [sr0] Add. Sense: Logical block address out of range
[388151.075884] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[388151.075902] end_request: I/O error, dev sr0, sector 0
[388151.078141] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[388151.078151] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[388151.078160] Info fld=0x400
[388151.078164] sr 1:0:0:0: [sr0] Add. Sense: Logical block address out of range
[388151.078173] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 04 00 00 00 02 00
[388151.078192] end_request: I/O error, dev sr0, sector 4096
[388151.097318] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[388151.097328] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[388151.097338] Info fld=0x0
[388151.097342] sr 1:0:0:0: [sr0] Add. Sense: Logical block address out of range
[388151.097353] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[388151.097371] end_request: I/O error, dev sr0, sector 0
[388151.099590] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[388151.099599] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[388151.099607] Info fld=0x0
[388151.099611] sr 1:0:0:0: [sr0] Add. Sense: Logical block address out of range
[388151.099621] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[388151.099639] end_request: I/O error, dev sr0, sector 0
[388151.105228] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[388151.105238] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[388151.105247] Info fld=0x0
[388151.105251] sr 1:0:0:0: [sr0] Add. Sense: Logical block address out of range
[388151.105261] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[388151.105279] end_request: I/O error, dev sr0, sector 0
[389174.144642] cdrom: This disc doesn't have any tracks I recognize!
[389248.000081] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[389248.000095] sr 1:0:0:0: [sr0] CDB: Write(10): 2a 00 00 06 f4 20 00 00 10 00
[389248.000125] ata2.00: cmd a0/01:00:00:00:80/00:00:00:00:00/a0 tag 0 dma 32768 out
[389248.000129]          res 40/00:03:00:0c:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[389248.000136] ata2.00: status: { DRDY }
[389248.000147] ata2: hard resetting link
[389248.484051] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[389248.494348] ata2.00: configured for UDMA/133
[389248.496052] ata2: EH complete
[389490.636943] sr 1:0:0:0: ioctl_internal_command return code = 8000002
[389490.636953]    : Sense Key : Hardware Error [deferred] 
[389490.636962]    : Add. Sense: Tracking servo failure

---

